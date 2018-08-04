# dwitter

A platform to write visual art in javascript limited to 140 characters.

Available on [dwitter.net](http://dwitter.net)

Join the chat on [Discord](https://discord.gg/r5nXDsQ)

[![license](https://img.shields.io/github/license/lionleaf/dwitter.svg)]()

Inspired by [arkt.is/t/](http://arkt.is/t/Yy53aWR0aD0yZTM7eC5maWxsUmVjdCgxNTAsMTUwKlModCkrMTUwLDE1MCwxNTAp)


## Pre-requisites and first-time installation
* Install `npm`
* `sudo apt install npm`
*  Get packages needed for server and clone the repository
* `sudo apt install git virtualenv python-pip`
* `git clone https://github.com/lionleaf/dwitter.git`

## Setup
* `make setup` (set up virtual environment)
* `source venv/bin/activate` (activate virtual environment)
* `make` (install dependencies and set up database)
* `python manage.py createsuperuser` (create admin account used below)
* `make run` runs the server. Use `make serve` instead if you're working inside a VM with port forwarding. (0.0.0.0:8000)
* Go to [http://localhost:8000/admin/sites/](http://localhost:8000/admin/sites/) and log in with admin account created above.
* Click on the one entry, and change both `domain name` and `display name` to localhost:8000.
* Make sure http://dweet.localhost:8000/ returns a django error. May not work in Firefox.

## Other commands
* `make migrations`
* `make migrate`
* `make lint`
  * lints Python and JS files
  * automatically fixes some JS issues (mostly whitespace-related)
* `make shell`
* `make backup`
* `make restore-backup`

## Local development on Firefox

If the dweets don't load on Firefox while devloping, you might need to set the 'network.dns.localDomains' string to 'dweet.localhost'. The option can be found by going to about:config. Note; this is only for Firefox when developing locally.

# Dwitter API

### Dweets
```
GET www.dwitter.net/api/dweets/  - list of the last 10 dweets
       
       ?limit=100            - number of results to return, default 10, max 100 (subject to change)
       &offset=200           - offset page by 200 dweets
       &remix_of=123         - all remixes of 123
       &author=lionleaf      - dweets by author


GET www.dwitter.net/api/dweets/123  - get details about d/123
```

Latest dweet: `https://www.dwitter.net/api/dweets/?limit=1`  (sorted by posted date by default)


### Users
```
GET dwitter.net/api/users/lionleaf  - Show details about user 'lionleaf'.
```
