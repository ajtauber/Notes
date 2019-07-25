# Rails - HABTM ASSOCIATIONS
## Setup

* gem 'pry-rails'
Make sure you add `gem 'pry-rails'` in your Gemfile

## Create project
Make a new rails file within `08-rails folder`
`rails new Tunr -T --skip-git -d postgresql`
`cd Tunr`
`atom .`
`bundle`


## Creating Databases
* First we create the database within our project
`rails db:create`
* Instead of using what we learned yesterday
`rails generate migration` we instead use `rails generate model`
This is a short-cut compared to `generate migration` it creates the model as well as the migration **together**
* We then look into the folder (*app/models/...*)
* Once we

### Songs Database

```
rails generate model Song title:text artist_id:integer album_id:integer
rails db:migrate
annotate
```


```
create    db/migrate/20190725003415_create_songs.rb
create    app/models/song.rb
```
### Creating Artist Table
```
rails generate model Artist name:text image:text
rails db:migrate
annotate
```

### Creating Album Table
```
rails generate model Album title:text image:text
rails db:migrate
annotate
```
*

### Creating Genre Table
```
rails generate model Genre name:text
rails db:migrate
annotate

```

### Creating Mixtape Table :notes:
```ruby
rails generate model Mixtape title:text user_id:integer
rails db:migrate
annotate
```
### Creating User Table
```
rails generate model User email:text
rails db:migrate
annotate
```


> You create something called a join table that ruby knows about but we haven't covered it yet - Joel

> When you join your entity in your relationships you can call your join table any name you want - Joel
> Lower case name in Alphabetical order - Joel

### Joining Tables
* We
`mixtapes_songs`
`genre_songs`
> Don't run rails generate model for the join
> We have to create the join tables
> We create another table with just the joined tables together and have nothing inside it
`rails generate migration create_mixtapes_songs mixtape_id:integer song_id:integer`

Now we go to the (*2019...._create_mixtapes_songs.rb*) and add `, :id => false`

  `create_table :mixtapes_songs, :id => false do |t|`


Do the same thing with genre_songs joined table
`rails generate migration create_genres_songs genre_id:integer song_id:integer`

Now we go to the (*2019...._create_genres_songs.rb*) and add `, :id => false`



### Songs.RB
`optional => true` makes it so there's no duplication within the database
If there are 2 Toxics by the same artist, they can't add it as its a duplicated version if `option => true` is being used

`belongs_to :artist, :optional => true`
`belongs_to :album, :optional => true`
`has_and_belongs_to_many :genres`
`has_and_belongs_to_many :mixtapes`

### Seeds.rb
```
User.destroy_all
u1 = User.create :email => 'craigsy@ga.co'
u2 = User.create :email => 'jonesy@ga.co'

puts "Creating songs"
Song.destroy_all
s1 = Song.create :title => 'Have A Safe Trip, Dear'
s2 = Song.create :title => 'Toxic'
s3 = Song.create :title => "Don't Ask Me To Dance"
s4 = Song.create :title => 'Gut Feeling'

Album.destroy_all
puts "Creating albums"
l1 = Album.create :title => 'Engine Takes To The Water'
l2 = Album.create :title => 'In The Zone'
l3 = Album.create :title => 'The Last Romance'
l4 = Album.create :title => 'Are We Not Men? We Are Devo'

Artist.destroy_all
puts "Creating Artists"
a1 = Artist.create :name => 'June of 44'
a2 = Artist.create :name => 'Britney Spears'
a3 = Artist.create :name => 'Arab Strap'
a4 = Artist.create :name => 'Devo'

Genre.destroy_all
puts "Creating Genre"
g1 = Genre.create :name => 'Nautical Text Rock'
g2 = Genre.create :name => 'Nautical Math Rock'
g3 = Genre.create :name => 'Folk Rock'
g4 = Genre.create :name => 'Scottish Misery Rock'
g5 = Genre.create :name => 'Bollywood Bubblegum Pop'
g6 = Genre.create :name => 'New Wave'

Mixtape.destroy_all
puts "Creating Mixtapes"
a1 = Mixtape.create :name => 'Driving Songs'
a2 = Mixtape.create :name => 'Makeout Music'
a3 = Mixtape.create :name => 'Code Jams'
a4 = Mixtape.create :name => 'Monkey Mongs'

```




```
rails generate migration add_password_digest_to_users password_digest:string

```

`rails generate controller User index new`

`rails db:seed`


`rails generate controller Session new`

We don't want this in our (* routes.rb *) file >> under the **config folder** `get 'session/new'`

### Moving onto the Log in Form within session

(*new.html.erb*)
* We create a form to allow us to efficiently move onto to the

```
<h1>Sign In</h1>

<%= flash[:error] %>

<%= form_tag login_path do %>
  <div class="form-row">
    <%= label_tag :email %>
    <%= email_field_tag :email, nil, :class => 'form-control' %>
  </div>

  <div class="form-row">
    <%= label_tag :password %>
    <%= password_field_tag :password, nil, :class => 'form-control' %>
  </div>

  <%= submit_tag "Sign in", :class => 'btn-lg btn-success' %>
<% end %>
```
### SessionController

```
  def create
    # find the user by their email address
    user = User.find_by :emails => params[:email]
    # encrypted password matches the encryped password in the database
    if user.present? && user.authenticat(params[:password])
      redirect_to root_path
    else
      flash[:error_message]
      redirect_to login_path  #  show them the login form
    end
  end

  def destroy
    # to log someone out we can forget their user_id but setting it to nothing (nil)
    session[:user_id] = nil
    redirect_to login_path
  end
```
### ApplicationController
* Before we do anything we need to fetch the users
* Now we move onto a private function --- we fetch the user with a current user finding the user by ID within the user session 
### Creating a Sign Out
```


```


### Validation
We covered validating each user having a specific email address
To allow someone to sign in, go to user_controller.rb `session[:user_id] = @user.id`
`user.present? && user.authenticate(params[:password])`
SessionController > @error = `Invalid email or password` -- Session_New --- Print out Error **It will be undefined** It wont work **instead use the magic variable** `flash[:error_message]`



```
def destroy

end

```




### Associations
