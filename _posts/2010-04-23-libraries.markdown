---
layout: default
title: API Libraries
---

## API Implementations ##

Libraries for accessing the GitHub API from your favorite language.

### C Sharp ###

[GitHubSharp][gs] looks pretty slick - hot off the press.

[gs]: http://github.com/erikzaadi/GithubSharp

### Java ###

[ghapi][ghj] is a Java library implementing much of v2 API and is
constantly being developed.

[ghj]: http://github.com/eddieringle/ghapi

[github-java-sdk][ghjsdk] is a type-safe Java implementation of the whole v2 API and has 
some additional support for OAuth authentication and reading ATOM feeds. Its actively under development.

[ghjsdk]: http://github.com/nabeelmukhtar/github-java-sdk

### Javascript ###

[github-api][ghjs] is a Javascript library with no dependencies for interop
with the github API. Currently supports a large portion of V2, with more to
come. Tries to map directly to the HTTP API, but in a JS style.

[ghjs]: http://github.com/fitzgen/github-api

The [node-github][ng] library is a port of [php-github-api][pga] to JavaScript for [node.js][node]. It provides an asynchronous object oriented API and is fully tested.

[ng]: http://github.com/ajaxorg/node-github
[node]: http://nodejs.org/

### Perl ###

The [Net::GitHub][net-perl-github] library for Perl encapsulates much
of the functionality of the GitHub v2 API.  You can also download it
from [CPAN][net-perl-cpan].

[net-perl-cpan]: http://search.cpan.org/dist/Net-GitHub/
[net-perl-github]: http://github.com/fayland/perl-net-github/tree/master


### PHP5 ###

The [php-github-api][pga] is fully tested and documented.

[pga]: http://github.com/ornicar/php-github-api

### Python ###

[Dustin Sallings'][dustin] [py-github][py-github] project was the
first third-party implementation of the v1 API and is tracking the v2
API in a branch as new API endpoints are published. [Fork
it][py-github] it and help keep it awesome.

There is alo a new Python library for the GitHub v2 API called
[python-github2][python-github2].  It has nearly the full API feature
list.

[Kenneth Reitz's][kennethreitz] [GistAPI.py][gistapi] is a Python wrapper for the Gist API. New Gist API features will be introduced as the API endpoints are published.

[dustin]: http://github.com/dustin
[kennethreitz]: http://github.com/kennethreitz
[py-github]: http://github.com/dustin/py-github
[python-github2]: http://github.com/ask/python-github2
[gistapi]: http://github.com/kennethreitz/gistapi.py

### Ruby ###

#### API Version 1 ####

The [github-control][github-control] library is currently doing work
using the v1 API. The aim is to build a library which others can build
on top of.

It currently has features which need to be enabled on the v2 API as
they were in pre-release when developed.

The [github-party][gh-party] library is also using the v1 API.

[github-control]: http://github.com/halorgium/github-control
[gh-party]: http://github.com/technicalpickles/github-party

#### API Version 2 ####

There are several active GitHub API v2 wrappers for Ruby: [octokit][ok], 
[octopi][octopi], and [hubruby][hubruby].

[octopi]: http://github.com/fcoury/octopi/
[ok]: http://github.com/pengwynn/octokit
[hubruby]: http://github.com/diogenes/hubruby

#### Web scraping ####

[halorgium][halorgium] built a wrapper around the current post-receive hooks UI.
It is called [github-post-receive-hooks][github-post-receive-hooks]
Based on a gist by [tekkub][tekkub].

[halorgium]: http://github.com/halorgium
[tekkub]: http://github.com/tekkub
[github-post-receive-hooks]: http://github.com/halorgium/github-post-receive-hooks


### Cocoa/Objective-C ###

[Clint Shryock's fork of CocoaREST][CocoaREST] extended the base CocoaREST library, a set of Cocoa classes to interact with RESTful services, to support Github's v1 API.

[GitHubObjC][GitHubObjC] is an Objective-C library implementing most of the GET requests of v2 API.

[UAGithubEngine][UAGithubEngine] is a Cocoa wrapper around version 2 of the Github API, written in Objective-C. It includes all functionality except the Network Graph and Gist APIs.

[CocoaREST]: http://github.com/ctshryock/CocoaREST
[GitHubObjC]: http://github.com/ernstsson/GitHubObjC
[UAGithubEngine]: http://github.com/owainhunt/UAGithubEngine
