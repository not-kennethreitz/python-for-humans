!SLIDE
# Python for Humans
(or something to that effect)

<!-- !SLIDE bullets incremental
#yay

- No ulterior motives.
- A call for reevaluate our values
- Most of the problems that we're going to discuss today are simple.
 -->



!SLIDE
# Philosophy.


!SLIDE
# We share a dark past:

Perl, Java, PHP, ColdFusion, Classic ASP, *&c*.


!SLIDE code
# The Zen of Python.
    >>> import this


!SLIDE
## Beautiful is better than ugly.


!SLIDE
## Explicit is better than implicit.


!SLIDE
## Simple is better than complex.


!SLIDE
## Complex is better than complicated.


!SLIDE incremental bullets
### If the implementation is hard to explain, it's a bad idea.

- <span class='smaller'>(except pypy)</span>


!SLIDE
### There should be one—and preferably only one—obvious way to do it.



!SLIDE
# Welcome to paradise.

!SLIDE
# <s>Welcome to paradise.</s>

!SLIDE red bigger
# LIES!










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
# Let's play around.

Maybe play with the GitHub API?


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















!SLIDE bullets incremental
# This is a serious problem.


!SLIDE bullets incremental
# The Solution is Simple.

- Build elegant tools to perform these tasks.
- Provide a real resource for learning.

!SLIDE
## Python needs more Pragmatic Packages.

!SLIDE dark

## pra•gmat•ic |pragˈmatik|, *adj*:
Dealing with things sensibly and realistically in a way that is
based on practical rather than theoretical considerations.

!SLIDE
# An Examples.

### Let's mess around. Maybe play with the GitHub API?
!SLIDE



!SLIDE small code

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

## Let's port this to Python.

!SLIDE smaller code execute
# Python (hours later).
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

!SLIDE smaller code execute
#I lied — there's more!

    @@@ python

    import re

    class HTTPForcedBasicAuthHandler(HTTPBasicAuthHandler):

        auth_header = 'Authorization'
        rx = re.compile('(?:.*,)*[ \t]*([^ \t]+)[ \t]+'
                        'realm=(["\'])(.*?)\\2', re.I)

        def __init__(self,  *args, **kwargs):
            HTTPBasicAuthHandler.__init__(self, *args, **kwargs)s

        def http_error_401(self, req, fp, code, msg, headers):
            url = req.get_full_url()
            response = self._http_error_auth_reqed(
                'www-authenticate', url, req, headers)
            self.reset_retry_count()
            return response

        http_error_404 = http_error_401

!SLIDE
# Admit it.

If this was you, you'd leave Python and never come back.


!SLIDE
# Break it down.



!SLIDE
# Enter Requests.



!SLIDE
# The Codez, they are ugleh.

[trollface or something]

!SLIDE
## Unless there's an explicit requirement,
## a student should never see urllib2.

# No excuses.

!SLIDE
# Pragmatic Package.

    @@@ python
    import requests

    url = 'https://api.github.com/user'
    auth = ('username', 'password')

    r = requests.get(url, auth=auth)
    print r.content


!SLIDE
# Fit the 90% Use Case.

!SLIDE
# The API is all that matters.

## Everything else is secondary.

!SLIDE incremental bullets
# I Mean ***Everything***.

- Features.
- Efficiency.
- Performance.
- Corner-cases.

!SLIDE
# urllib2

"I'd rather be writing ColdFusion."

!SLIDE small
# subprocess

A powerful module that .

    @@@ python
    import envoy

    c = envoy.run('ls')
.

    @@@ pycon
    >>> c.status_code
    200











!SLIDE
## The Hitchhiker's Guide to Python

http://python-guide.org

!SLIDE code top
![DON'T PANIC](ext/dont-panic.jpeg)


!SLIDE
- A guidebook for newcomers.
- A reference for seasoned veterans.

!SLIDE
# There's only one rule.

!SLIDE
> There should be one—and preferably only one—obvious way to do it.

!SLIDE
# Topics

!SLIDE
# Installing Python Properly

!SLIDE
# Installing

!SLIDE
# Installing Python Properly

!SLIDE
# Installing Python Properly

!SLIDE small
# Best Practices

- Will recommend **distribute**, **pip**, and **virtualenv** out of the box.
Explicit directions for setup on every major OS.
- Instill a resistance to `doctest`
- Teach `datetime.utcnow()`


!SLIDE small
# Installation Guides

- PIL
- Python-MySQL