# Secrets Server
* open in atom
* go to the Gem File
* Add `gem rack-cors` in Gem file
* run bundle install
* Go in `config>initializer`
* add `cors.rb` inside `initializer`

```
Rails.application.config.middleware.insert_befor 0, Rack::Cors do
  allow do
    origins '*'
    resource '*',
      :headers => :any,
      :methods => %i( get post put patch delete options head ) # array of symbols
  end
end
```
```
App>controller>application_controller.rb
skip_before_action: verify_authenticity_tocken
```
# Secret Client

* `ngrok 3000`

```
// const SERVER_URL = 'http://localhost:3000/secrets.json';

const SERVER_URL = 'http://ca0ca0c4.ngrok.io/secrets.json';
```
