## Sinatra versus Rails Exploration

### Setup:

First, clone down the Rails project:

```terminal
git clone https://github.com/turingschool/job-tracker.git rails_project
```

And then clone down the Sinatra project:

```terminal
git clone https://github.com/turingschool/bike-share.git sinatra_project
```
Now cd into each project, run `bundle` on each project, and you're ready to go. We will only be looking at the code base and not interacting with the app. If you wanted to run the server and interact with the app, you would need to create your database, migrate your migrations, etc.

### Exercise:

1. Take a look at this stripped down Sinatra app and this stripped down Rails app. How are they different and how are they similar? Identify 5 differences, and for each one describe 1-2 implications. What effect does that difference have for each framework? If you don't know exactly, draw on your knowledge and experience and make some educated guesses/inferences. Also, practice your research skills to look into the differences.

They are similar in X, but different in y.
Sinatra has an MVC breakdown in app, db that holds csvs and migrations, spec with model, feature, and controller tests, with a spec helper. config.ru, gemfile, and rakefile.
Rails has the MVC model in the app...but also lots of other stuff. Mailers, helpers, assets (probably images and stuff, JS). Also controllers has multiple files!
Models look to be set up similarly.

Differences:
* Item - Public folder in Rails (at same level as app) with what looks like response pages - versus "Sinatra doesn't know this ditty." This gives Rails and consistent and more professional way of handling unknown routes (but how would a deployed Sinatra app handle this?)
* Item - More subdirectories in the config folder in Rails (environments, initializers, locales, and a bunch of other yml and rb items)
* Item - Gems - hard to describe, but when running bundle and looking at the output, it seems that Rails' gems sets up a lot more things for you
* Item - Rails has a bin directory - *[look up what this is]*
* Item - Controllers - Rails has a Application Controller that seems to be the main one, and then the other two (Companies and Jobs) inherit from it. It seems that paths are handled more simply in Rails - rather than the path/verb combo, the methods are broken out by CRUD functionality (looking at the Company Controller). I would guess that the order of the methods doesn't matter the way it did in the Sinatra controller, and that the different controllers serve different parts of the app *[look this up]*
* Item - Not sure if specific to Rails or an ERB thing, but the views seem to reference a form that is stored separately. And all files are appended with `.html.erb` *[look this up]*

2. Consulting blogs and commentary you find online, identify 3 similarities between Rails and Sinatra.

Similarities:
* First - Both can be used to build most applications (though you'll want to choose based on what your needs are, how experienced you are, and so on)
* Second - Both *can* be changed to suit your needs (though Sinatra much more flexible)
* Third - Both *can* follow an MVC framework - but Rails must follow it

3. Consulting blogs and commentary you find online, identify 3 things that distinguish Rails, advantages.

Advantages:
* Can use it for bigger-scale projects, full integration, lots of tools (though sometimes too many, and the wrong ones for the job)
* Can save time implementing features (especially ones you don't realize you need at the start)
* More robust security out of the box (Sinatra can leave lots of holes)
* Can provide faster development

4. In your Rails project, what does the `routes.rb` file inside of the `/config` directory do? What does this correlate to in our Sinatra app?

In the Rails project, the `routes.rb` in the `/config` takes in URLs and dispatches them to the controller, and it has the ability to generate paths and URLs so you don't have to hardcode them in your form. [Link here](http://guides.rubyonrails.org/routing.html). In the Sinatra app, this is something the controller does, taking in the URL route and coordinating the correct action(s).

5. We teach Sinatra by adding some structures that Sinatra doesn’t need, but help you make the transition between Sinatra and Rails. What does a stripped down implementation of Sinatra look like, and what are the pieces we’ve added for educational purposes?

A stripped down Sinatra implementation (if I am interpreting the question correctly) looks like it requires almost nothing:
```ruby
# myapp.rb
require 'sinatra'

get '/' do
  'Hello world!'
end
```
And in terminal:
```
gem install sinatra
```
and
```
ruby myapp.rb
```
Then you just visit `http://localhost:4567`. 
So, the added pieces include the MVC model, all the gems, the config (to use with a database, which you don't necessarily have to with Sinatra), the db folder, spec for testing, and probably some other things.
