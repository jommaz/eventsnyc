# Eventsnyc - THIS GEM IS BEING DEVELOPED THROUGH README-DRIVEN DEVELOPMENT IT IS NOT YET COMPLETE

**eventsnyc is a ruby gem that provides information on events that are taking place throughout New York City through 3 different APIs on chosen date. These are EventBrite, NYTimes Events & the official NYCGO events.

Before you use this Gem, you will need API keys from Eventbrite, NYtimes & NYCO. These can be obtained by making accounts at the following addresses:

http://developer.eventbrite.com/
http://developer.nytimes.com/docs/events_api
https://developer.cityofnewyork.us/api

All information will come back in the JSON format.

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'eventsnyc'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install eventsnyc

## Usage

To set your API key for each API in a safe manner, following this guide:
https://medium.com/wdi-nyc-jan-2014/keeping-api-keys-secret-in-ruby-on-rails-6ddb0793d281

Now that you have a global constant set for each API, you can will need to use the following syntax in your controller to begin using them:

```
Eventbrite_API_key = EVENTBRITE_CLIENT_ID
```

```
NYtimes_API_key = NYTIMES_CLIENT_ID
```

```
NYCgo_API_key = NYCGO_CLIENT_ID
```

To call on the Eventbrite API set a client instance variable with the following command in your controller:

```
ebclient = Eventbrite::Client:New
```

Once you have this set, set another instance variable for the start date & end date by passing an argument in the following manner (I have used an example of @funday.date, which would be obtained from the user through a form):

```
@events = ebclient.date(@funday.date)
```

The events obtained are on a specified date, returning all events within 24 hours.

Now that you have this set, you can iterate through the events in the following manner:

```
@events["events"]
```

The NYTimes & NYCgo calls are set up in the same manner as above but to iterate through them, you will require the following syntax:

For NYtimes:
```
@events["results"]
```

For NYCgo:
```
@events["items"]
```

To extract further information, I recommend reading the API documentation provided by the respective providers.


## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake rspec` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment. Run `bundle exec eventsnyc` to use the gem in this directory, ignoring other installed copies of this gem.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/jommaz/eventsnyc. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](contributor-covenant.org) code of conduct.


## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).

