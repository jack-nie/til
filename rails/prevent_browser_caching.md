###How to prevent browser page caching in Rails

Q: if you hit the back button, you don't see the new page. Unfortunately, it's not showing up without a manual refresh; it appears the browser is caching it. I want to make sure the browser does not cache the page.

A:

```
class ApplicationController < ActionController::Base

  before_filter :set_cache_headers

  private

  def set_cache_headers
    response.headers["Cache-Control"] = "no-cache, no-store, max-age=0, must-revalidate"
    response.headers["Pragma"] = "no-cache"
    response.headers["Expires"] = "Fri, 01 Jan 1990 00:00:00 GMT"
  end
end
```

* Link: [how-to-prevent-browser-page-caching-in-rails](http://stackoverflow.com/questions/711418/how-to-prevent-browser-page-caching-in-rails "how-to-prevent-browser-page-caching-in-rails")
