## Issues API ##

The API for GitHub Issues.

### Search Issues ###

	/issues/search/:user/:repo/:state/:search_term

Where 'state' is the 
For example, to search for 'test' in the open issues for defunkt/github-issues repo, you can do this:

	$ curl http://github.com/api/v2/json/issues/search/defunkt/github-issues/open/test 
	{
	  "issues": [
	    {
	      "user": "kfl",
	      "updated_at": "2009\/04\/20 03:34:48 -0700",
	      "votes": 3,
	      "number": 102,
	      "title": "Pressing question-mark does not show help",
	      "body": "Pressing the '?'-key does not open the help lightbox.\r\n\r\nHowever, at least the 'j', 'k', and 'c' works (the only ones I've tested).\r\n\r\n* **OS:** Linux, ubuntu 8.04.1\r\n* **Browser:** Firefox 3.08",
	      "state": "open",
	      "created_at": "2009\/04\/17 12:57:52 -0700"
	    }
	  ]
	}


### List a Projects Issues ###

To see a list of issues for a project,

	issues/list/:user/:repo/:state

where :state is either 'open' or 'closed'.

For example, to see all the open issues I have on the schacon/simplegit project, we can run

	$ curl http://github.com/api/v2/yaml/issues/list/schacon/simplegit/open
	--- 
	issues: 
	- number: 1
	  votes: 0
	  created_at: 2009-04-17 14:55:33 -07:00
	  body: my sweet, sweet issue
	  title: new issue
	  updated_at: 2009-04-17 14:55:33 -07:00
	  user: schacon
	  state: open
	- number: 2
	  votes: 0
	  created_at: 2009-04-17 15:16:47 -07:00
	  body: the body of a second issue
	  title: another issue
	  updated_at: 2009-04-17 15:16:47 -07:00
	  user: schacon
	  state: open


### View an Issue ###

To get data on an individual issue by number, run 

	issues/show/:user/:repo/:number

So to get all the data for a issue #1 in our repo, we can run something like this:

	$ curl http://github.com/api/v2/yaml/issues/show/schacon/simplegit/1
	--- 
	issue: 
	  number: 1
	  votes: 0
	  created_at: 2009-04-17 14:55:33 -07:00
	  body: my sweet, sweet issue
	  title: new issue
	  updated_at: 2009-04-17 14:55:33 -07:00
	  user: schacon
	  state: open


### List an Issue's Comments ###

To get a list of comments made on an issue, run

	issues/comments/:user/:repo/:number

So to get all the comments for a issue #1 in our repo, we can run something like this:

    $ curl http://github.com/api/v2/yaml/issues/comments/schacon/simplegit/open
    --- 
    comments: 
    - created_at: 2010-02-08 12:54:54 -08:00
      body: this is a really great idea
      updated_at: 2010-02-08 12:54:54 -08:00
      id: 1
      user: defunkt
    - created_at: 2010-02-08 12:55:05 -08:00
      body: is it?
      updated_at: 2010-02-08 12:55:05 -08:00
      id: 2
      user: schacon


### Open and Close Issues ###

To open a new issue on a project, make a authorized POST to

	issues/open/:user/:repo

Where you can provide POST variables:

	title 
	body

It will return the data for the newly created ticket if it is successful.  You need to provide your username and token so the system knows who you are and can assign you as the opener of the issue.

For example, I could open a new issue on my simplegit project like this:

	$ curl -F 'login=schacon' -F 'token=XXX' -F 'title=new' -F 'body=my ticket' \
	 	http://github.com/api/v2/yaml/issues/open/schacon/simplegit
	--- 
	issue: 
	  user: schacon
	  body: my ticket
	  title: new
	  number: 1
	  votes: 0
	  state: open

To close or reopen an issue, you just need to supply the issue number

	issues/close/:user/:repo/:number

	issues/reopen/:user/:repo/:number

You need to be logged in via token as well.  Here is how I would close the ticket I opened earlier:

	$ curl -F 'login=schacon' -F 'token=XXX' \
		http://github.com/api/v2/yaml/issues/close/schacon/simplegit/1
	--- 
	issue: 
	  user: schacon
	  body: 
	  title: new
	  number: 1
	  votes: 0
	  state: closed

### Edit Existing Issues ###

For the final three calls (edit, label add and label delete) you have to be authorized a collaborator on the project.

To edit an existing issue, you can POST to

	issues/edit/:user/:repo/:number

Where you can provide POST variables:

	title 
	body

This will overwrite the title or body of the issue, if you are authorized member of the project.

### Listing Labels ###

You can list available labels for a projects issues with

	issues/labels/:user/:repo

For example,

	$ curl -F 'login=schacon' -F 'token=XXX' https://github.com/api/v2/yaml/issues/labels/schacon/simplegit
	---
	labels:
	- label1
	- label2

### Add and Remove Labels ###

To add a label, run

	issues/label/add/:user/:repo/:label/:number

This will return a list of the labels currently on that issue, your new one included. If the label is not yet in the system, it will be created.  

Here is how I would add the label 'testing' to my first ticket in my simplegit project:

	$ curl -F 'login=schacon' -F 'token=XXX' https://github.com/api/v2/yaml/issues/label/add/schacon/simplegit/testing/1
	--- 
	labels: 
	- testing
	- test_label


To remove a label, run:

	issues/label/remove/:user/:repo/:label/:number

Again, it will return a list of the labels currently on the issue.

### Comment on Issues ###

You can comment on issues at

	/issues/comment/:user/:repo/:id 

Simply send it a 'comment' POST variable with the comment you'd like to make.  It will attribute the comment to the user that is authenticated.  Here is an example:

	$ curl -F 'login=schacon' -F 'token=XXX' -F 'comment=this is amazing' \
	  https://github.com/api/v2/json/issues/comment/defunkt/dunder-mifflin/1 
	{"comment": {"comment": "this is amazing", "status": "saved"}}
