Develop.GitHub.com
==================

This is the code and data behind <http://develop.github.com>.

All content can be found in the _posts/ direcotry.


Dependencies, Getting Started
-----------------------------

Install [Jekyll][jk] an rake (both require Ruby):

    gem install jekyll rake

Once you've done that, run `rake` to compile the site:

    rake

This should start a web server at <http://localhost:3000> which is now
serving your site, updating whenever you make changes.

Contributing
------------

To contribute to the develop.github site, you can fork the repository,
push your changes into it and create an Issue:
<http://github.com/develop/develop.github.com/issues>

If you want to run the site on GitHub pages for testing you can push your
changes into the 'gh-pages' branch, rather than the 'master' branch of
the remote repository.

    $ git push origin master:gh-pages

That command will push your master branch to the 'gh-pages' branch of
your fork.  Then Pages will serve the site for you under:

<http://schacon.github.com/develop.github.com>

(Replace 'schacon' with your username)
