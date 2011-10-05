!SLIDE
# Let's Build Things.

Python needs more Pragmatic Packages.

!SLIDE small

pra•gmat•ic |pragˈmatik|,
*adj*, dealing with things sensibly and realistically in a way that is
based on practical rather than theoretical considerations.

!SLIDE
# Some Examples

!SLIDE
# NOT PRACTICAL

[fucking urllib2 code]

!SLIDE
# NOT PRACTICAL (cont)

!SLIDE
# Practical.

    @@@ ruby

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
# Fit the 90% Use Case.

!SLIDE
# urllib2

"I'd rather be writing ColdFusion."

!SLIDE
# subprocess
- envoy