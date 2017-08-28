# ui-components-angularjs
Using different components from the Bootstrap Framework to have an elegant UI.


#### Part 1: Navigation Bar

1) Go the [bootstrap website](https://getbootstrap.com/) and check the documentation and samples.


2) Follow the *Getting started* tutorial under the *Documentation* section and create a basic html page that uses at least 4 different components:
* Navbar
* Modal 
* Progress
* Free Choice Element

2) Download the project provided in the repo, run the commands below and make sure it works:

    ```` bash 
    npm install
    npm start
    ````
    
3) Modify *app.component.html* in the given project so it contains the following navbar that includes a search input:

    ````html
        <nav class="navbar navbar-expand-lg navbar-light bg-light">
          <a class="navbar-brand" href="#">Navbar</a>
          <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button>
        
          <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav mr-auto">
              <li class="nav-item active">
                <a class="nav-link" href="#">Home <span class="sr-only">(current)</span></a>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="#">Link</a>
              </li>
              <li class="nav-item">
                <a class="nav-link disabled" href="#">Disabled</a>
              </li>
            </ul>
            <form class="form-inline my-2 my-lg-0">
              <input class="form-control mr-sm-2" type="text" placeholder="Search" aria-label="Search">
              <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Search</button>
            </form>
          </div>
        </nav>

    ```` 
    
    
3) Add a modal that has the following message "This feature is not implemented yet. Sorry for the inconvenience" and add the logic to display it when the user clicks the *search* button.


#### Part 2: Users and Images

1) Navigate */src/app/models* and create a *User* model class:

    ```` TypeScript
        export class User {
            private name: string;
            private lastname: string;
            private image: string;
        
            constructor(name: string, lastname: string, image: string) {
                this.name = name;
                this.lastname = lastname;
                this.image = image;
            }
        }
    ````
    

2) Navigate */src/app/pages* and create the *user-list-page* package and inside create the following files:

* user-list-page.component.css
* user-list-page.component.html
* user-list-page.component.ts

3) Modify the content of *user-list-page.component.html* so it displays the user's info in a table. In order to display the user image use the following code:

    ````html
        <td><img [src]="user.image" width="150" height="150" /></td>
    ````
**Notice that the user image is a url that points to an existing image on the web.    


4) Modify the content of *user-list-page.component.ts* so it handles the users list logic (have a look at the *task-list-page.component.ts* for some inspiration).

5) Navigate */src/app/pages* and create the *user-edit-page* package and inside create the following files:
   
   * user-edit-page.component.css
   * user-edit-page.component.html
   * user-edit-page.component.ts

6) Modify the content of *user-edit-page.component.html* so it contains a form to capture the user's data.

7) Modify the content of *user-edit-page.component.ts* so it contains the logic to add users (have a look at the *task-edit-page.component.ts* for some inspiration).

8) Navigate to */src/app/services* and create a service *users.service.ts*  to handle the requests to create and list the users.

    If you want to avoid having to start the SpringBoot project you can add the following mocked code to your methods to skip the security (use this only for testing locally).
 
    ````TypeScript
         
        login(username: string, password: string) {
           // Mock
           this.authService.accessToken = 'test_access_token';
           return Observable.of({ access_token: this.authService.accessToken });
        ...
        
        list(): Observable<User[]> {
            // Mock
            return Observable.of(this.users);
        ...
            
        create(name: string, lastname: string, image: string) {
          // Mock
          this.users.push(new User(name, lastname, image));
          return Observable.of({});  
        ...
    ````    

#### Part 3: Users API

1) Open Spring Boot Project from the previous code lab.

2) Add the missing *image* attribute to the *User* model.

3) Implement the logic of the *createUser* method in the *UserServiceImpl* 

4) Implement the endpoint required to retrieve the users list in the *UserController*

    ````Java
    @RequestMapping( value = "/items", method = RequestMethod.GET )
    public List<User> getUsers(){
    }
    ````
5) Implement the method *registerUser* so it calls the proper method of the *UserService*

6) Comment the Mock code of the Angular project and add the proper implementation to call the API in the login, list and create methods inside the *users.service.ts*.

7) Finally compile the angular project and include the compile output files into the *resources/static* folder of the Spring Boot project. Test and verify that it works correctly :D .


#### Bonus: master your skills and prove yourself that you actually understand
4) Implement a call to the server so when the search button is pressed then the method *findUserByEmail* of the Users API is called. A user that has an email that matches the query should be displayed inside the dialog. If no user is found then display a message saying "No user found with the email address".