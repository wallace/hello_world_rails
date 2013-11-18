## README

This is an example of using Ruby 2.0 Tracepoint API to measure the amount of
ruby and C method calls using rails.

Inspired by [Mark Bates's](https://twitter.com/markbates) [rubyconf presentation on tracepoint](http://www.slideshare.net/markykang/mangling-ruby-withtracepoint). Derived from [his code in the same talk](https://gist.github.com/markbates/7403345). Thanks [Mark](http://metabates.com/).

All requests are made against webrick placing rails using the production
environment.

Rails makes [27038](https://github.com/wallace/hello_world_rails/blob/master/rails_startup.out#L1581) calls on "startup[0]."

Rails makes [42174](https://github.com/wallace/hello_world_rails/blob/master/rails_startup_and_call.out#L3150) calls for startup and respond to one HTTP request via curl.

Therefore Rails makes 15,136 calls to process one curl HTTP request.

Rails makes [48907](https://github.com/wallace/hello_world_rails/blob/master/rails_startup_and_call_with_chrome_request.out#L3179) calls for startup and respond to one HTTP request via Google Chrome.

Therefore Rails makes 6,733 more calls to process one a Google Chrome HTTP request versus a command line curl request.

Rails makes [25509](https://github.com/wallace/hello_world_rails/blob/master/rails_startup_no_turbo.out#L1572) call on startup with turbolinks turned off.

Rails makes [40046](https://github.com/wallace/hello_world_rails/blob/master/rails_startup_and_call_no_turbo.out#L3088) calls on startup and respond to one HTTP request via curl with turbolinks off.

Rails makes [43135](https://github.com/wallace/hello_world_rails/blob/master/rails_startup_and_call_with_chrome_request_no_turbo.out#L3106) calls on startup and respond to one HTTP request via curl with turbolinks off.

Therefore Rails makes 14,537 calls to process one curl HTTP request with
turbolinks turned off.

[0] The method_call_collector.rb is loaded as an initializer in all cases. This
is towards the end of the rails initialization process but we're only interested in the difference between the amount of calls between a start up and a start up with one response, this is acceptable.
