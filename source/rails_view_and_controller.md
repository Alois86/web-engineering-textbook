Rails Views and Controller
==========================

what is this about?

After reading this guide you should

* know something
* be able to do something

-------------------------------------------------------

The View
--------

### view in MVC

* responsible for displaying stuff
* both web designers and developers might work on these files!


### rails views

* are stored in `app/views/<name of controller>/*.html.erb`
* template format `.erb` is html with embedded ruby:
* `<% ruby code here %>` just evaluates the code
* `<%= ruby code here %>` evaluates the code and includes result
* main template (for header, footer) in `app/views/layouts/application.html.erb`
* `yield`s to include single view


### static content

* anything placed in `public`
* is directly accessible in the web space, without going through rails!


### links

* never write links to your own app "by hand"!
* use helper methods to get the right URLs
* `link_to 'link text here', object` links to show action of the object
* use `rake routes` to find out the names of urls/paths


### Now do 'Rails for Zombies' Episode no3

![Rails for Zombies Episode 4](images/rails-for-zombies-4.jpg)

The Controller
--------------


### restful resources

a rails convention about which http methods and urls
you should use, and which controllers and methods you should use.

in `config/routes.rb`  

``` ruby
resources :zombies
```


![scaffold](images/rest.png)


``` 
GET    /zombies          zombies_controller def index
POST   /zombies          zombies_controller def create
GET    /zombies/new      zombies_controller def new
GET    /zombies/:id/edit zombies_controller def edit
GET    /zombies/:id      zombies_controller def show
PUT    /zombies/:id      zombies_controller def update
DELETE /zombies/:id      zombies_controller def destroy
```



### Now do 'Rails for Zombies' Episode no 4

![Rails for Zombies Episode 4](images/rails-for-zombies-4.jpg)

### nested resources #


### card belongs_to board

* one model belongs to another, and is dependent
* `has_many :cards, :dependent => :destroy`
* makes sense to nest urls:
* /boards/3/cards  - all the cards in board 3


Routes
-------


### routes file:

``` ruby
resources :boards do
  resources :cards
end
```

### Routes constructed by nested resources

``` sh
GET    /boards                          
POST   /boards                          
GET    /boards/new                      
GET    /boards/:id/edit                 
GET    /boards/:id                      
PUT    /boards/:id                      
DELETE /boards/:id                      
GET    /boards/:board_id/cards          
POST   /boards/:board_id/cards          
GET    /boards/:board_id/cards/new      
GET    /boards/:board_id/cards/:id/edit 
GET    /boards/:board_id/cards/:id      
PUT    /boards/:board_id/cards/:id      
DELETE /boards/:board_id/cards/:id      
```

Further reading
----------------

* Rails Guide: [Layouts and Rendering in Rails](http://guides.rubyonrails.org/layouts_and_rendering.html)
* Rails Guide: [Action Controller Overview](http://guides.rubyonrails.org/action_controller_overview.html)
* Rails Guide: [Rails Routing from the Outside In](http://guides.rubyonrails.org/routing.html)
* [link_to](http://apidock.com/rails/v3.2.8/ActionView/Helpers/UrlHelper/link_to)
* [before_filter](http://apidock.com/rails/AbstractController/Callbacks/ClassMethods/before_filter)
* [resources](http://apidock.com/rails/ActionDispatch/Routing/Mapper/Resources/resources)
