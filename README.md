# FeedSearcher [![Build Status](https://travis-ci.org/fastladder/feed_searcher.png?branch=master)](https://travis-ci.org/fastladder/feed_searcher) [![Code Climate](https://codeclimate.com/github/fastladder/feed_searcher.png)](https://codeclimate.com/github/fastladder/feed_searcher) [![Coverage Status](https://coveralls.io/repos/fastladder/feed_searcher/badge.png?branch=master)](https://coveralls.io/r/fastladder/feed_searcher)
Search RSS feed URLs from the given URL.


## Installation
```
$ gem install feed_searcher
```


## Usage
```ruby
require "feed_searcher"

FeedSearcher.search("https://github.com/fastladder/feed_searcher")
#=> ["https://github.com/fastladder/feed_searcher/commits/master.atom"]

FeedSearcher.search("https://github.com/fastladder/feed_searcher/commits/master.atom")
#=> ["https://github.com/fastladder/feed_searcher/commits/master.atom"]
```


## Internal
Let me explain how FeedSearcher works along its execution sequence.

1. Fetches the HTML source of the given URL
2. Finds link elements (represented as XPath format)
3. Extracts URLs from the elements via its `href` attribute
4. Includes the given URL if its resource itself is a feed
5. Converts from relative path to absolute path
