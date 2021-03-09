# Single Action Classes  
<p class="mx-auto fit-content p-3"><img src="/laravel.docs/images/singleAction.svg" height="120"/></p>

### Routes
It all starts with a route.
```
Route::get('/', [Countrycontroller::class, 'index'])->name('countries.index');
```
### Controllers on diet
A controller (child ) extends a BaseController abstract class (parent) which:
* Captures the request in a magic call method if the requested method does not exist in the child controller.
* Validates if a request class exists and if it exists the arguments would be captured as: 


```
array $request->validated();
```
* Forwards the request to an action class which respond with an object containing:
  * A success attribute boolean (true/false).
  * A message attribute.
  * An errors array, empty by default.
  * A data attribute.
  * A meta array if required.
* Responds with a serialized to json object.  


### Action class
The action benefits from a single public method named 'execute'.  
The method 'execute' accept one argument which can be:
* An array of arguments that can be destructured as:
  

  ```
  public function execute(array $args) {
    list(
        'id' => $id,
        'name' => $name,
    ) = $args;
    .
    .
    .
  }
  ```
* A request instance could be also used as a single argument which potentially combines:
  * A file raw data in case the action is used to upload.
  * And the validated arguments coming from the request class.
    

    ```
    public function execute(Request $request) {
        list(
            'id' => $id,
            'name' => $name,
        ) = $request->validated();
        
        //File raw data: $request->file('originalFileName'); 
        .
        .
        .
    }
    ```
  * The action class is responsible to:
    * Process the business logic as DB queries, Api calls ...
    * Cache the data;
    * Transform the data with a transformer class
    * Event
    * ... etc.
  * Format the response back to the BaseController.
    

    ```
   /**
     * @param array $data
     * @return $this
     */
    private function formResponse(array $data): self
    {
        $this->success = true;

        $this->data = $data;

        return $this;
    }
    ```



### Assumptions

#### Naming convention
With the abstraction done in the BaseController methods the following naming convention should be respected.  

<table>
<tbody>
<tr><td>Controller method name</td><td>methodName</td></tr>
<tr><td>Request class name</td><td>MethodNameRequest</td></tr>
<tr><td>Action class name</td><td>MethodNameAction</td></tr>
<tr><td>Action class method name</td><td>execute</td></tr>
</tbody>
</table>

#### Child controller
1- The child controller should contain two arguments to indicate the path to the request classes and the action classesl
```
    protected string $requestBasePath = 'App\\Http\\Requests\\Countries';

    protected string $actionBasePath = 'App\\Actions\\Countries';
```
2 - A developer can opt to overwrite all the above by creating a method in the child controller class.
