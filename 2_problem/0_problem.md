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

!SLIDE smaller code execute
# Python.
    @@@ python
    import urllib2

    gh_url = 'https://api.github.com/user'

    req = urllib2.Request(gh_url)

    password_manager = urllib2.HTTPPasswordMgrWithDefaultRealm()
    password_manager.add_password(None, gh_url, 'user', 'pass')

    auth_manager = urllib2.HTTPBasicAuthHandler(password_manager)
    opener = urllib2.build_opener(auth_manager)

    urllib2.install_opener(opener)

    handler = urllib2.urlopen(req)

    print handler.read()

!SLIDE
# http/url/lib/2



!SLIDE
# Step 3: Install Packages.

* MySQL-Python


!SLIDE
# Common Pitfalls
* easy_uninstall?

!SLIDE
# Installing Dependencies

* Pip? Virtualenv? Never mentioned in the docs.
* python-mysql
* mod_wsgi

# Integration Time

!SLIDE
# PIL

(On OSX, this is simple)

