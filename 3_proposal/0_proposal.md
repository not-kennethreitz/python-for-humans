!SLIDE
# Let's Build Things.

Python needs more Pragmatic Packages.

!SLIDE dark

## pra•gmat•ic |pragˈmatik|, *adj*:
Dealing with things sensibly and realistically in a way that is
based on practical rather than theoretical considerations.

!SLIDE
# Some Examples

!SLIDE
# NOT PRACTICAL

[fucking urllib2 code]

!SLIDE
# NOT PRACTICAL (cont)


!SLIDE
# The Codez, they are ugleh.

[trollface or something]

!SLIDE
## Unless there's an explicit requirement,
## a student should never see urllib2.

# No excuses.

!SLIDE
# Practical.

    @@@ ruby
    ruby codez

!SLIDE
# Pragmatic.

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

!SLIDE incremental
# Everything.

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
