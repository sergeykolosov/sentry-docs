---
name: Rack
doc_link: https://docs.sentry.io/platforms/ruby/guides/rack/
support_level: production
type: framework
---

### Installation

Install the SDK via Rubygems by adding it to your `Gemfile`:

```ruby
gem "sentry-ruby"
```

### Configuration

Add `use Sentry::Rack::CaptureExceptions` to your `config.ru` or other rackup file (this is automatically inserted in Rails):

```ruby
require 'sentry-ruby'

Sentry.init do |config|
  config.dsn = '___PUBLIC_DSN___'

  # Set traces_sample_rate to 1.0 to capture 100%
  # of transactions for performance monitoring.
  # We recommend adjusting this value in production.
  config.traces_sample_rate = 1.0
  # or
  config.traces_sampler = lambda do |context|
    true
  end
end

use Sentry::Rack::CaptureExceptions
```
