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

1) Navigate */src/app/models* and create a User model:

    ```` TypeScript
        ng g class user
    ````