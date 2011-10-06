
!SLIDE
# Part II: Beginnings

So, let's say we're new to Python.

Let's get started!

!SLIDE
# Step 1: Pick a Release.
Pick carefully.


!SLIDE incremental
# Step 2: Install Python.

Decisions, decisions.

* Download installer from python.org?
* 32bit or 64bit?
* Build from source?
* If so, Unix or framework build?

!SLIDE
# Step 3: Profit!

Let's play around. Maybe play with the GitHub API?


!SLIDE small code execute
# Ruby.
    @@@ ruby
    require 'net/http'
    require 'uri'

    uri = URI.parse('https://api.github.com/user')

    http = Net::HTTP.new(uri.host, uri.port)
    http.use_ssl = true

    req = Net::HTTP::Get.new(uri.request_uri)
    req.basic_auth('username', 'password')

    r = http.request(req)

    puts r

!SLIDE
# http/url/lib/2
- Extremely unclear why there are so many modules.
- Search implies urllib2.
- Let's give this a shot...




!SLIDE
# http/url/lib/2

- Which module to use?
- Worst API ever.
- An *extremely* common use case.
- I'd rather be writing ColdFusion™.

!SLIDE
# XML

- `etree` is terrible.
- `lxml` is awesome, but difficult to install.

!SLIDE
# File and System Operations
- sys | shutils | os | os.path | io
- Really difficult to run external commands.
- This blocks dev+ops folks from adopting Python.

!SLIDE
# Packaging and Depdencies
- pip or easy install?
- setuptools isn't included with python? Distribute?
- No easy_uninstall?
- Broken `setup.py`s
- "Released" packages not in the Cheeseshop

!SLIDE
# Date[time]s.
- Which module to use?
- Timezones
- The stdlib can generate but not parse ISO8601 dates

!SLIDE
# Unicode.
- LOLWUT

!SLIDE
# Testing.


!SLIDE
# Installing Dependencies

* Pip? Virtualenv? Never mentioned in the docs.
* python-mysql
* mod_wsgi

!SLIDE
# Integration Time

!SLIDE
# PIL

(On OSX, this is simple)

