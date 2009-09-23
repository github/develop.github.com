## Users API ##

API for accessing and modifying user information.

### Searching for Users ###

The route for user searching is:

	  /user/search/:search

For instance, you would search for users with 'chacon' in their name like this:

	$ curl -i http://github.com/api/v2/xml/user/search/chacon

### Getting User Information ###

You can then get extended information on users by their username.  The url format is:

	  /user/show/:username [GET]

so the following command

	$ curl -i http://github.com/api/v2/yaml/user/show/defunkt

will return the something like this:

	user: 
	  id: 23
	  login: defunkt
	  name: Kristopher Walken Wanstrath
	  company: LA
	  location: SF
	  email: me@email.com
	  blog: http://myblog.com
	  following_count: 13
	  followers_count: 63
	  public_gist_count: 0
	  public_repo_count: 2

If you authenticated as that user, you will also get this information:
	
	  total_private_repo_count: 1
	  collaborators: 3
	  disk_usage: 50384
	  owned_private_repo_count: 1
	  private_gist_count: 0
	  plan: 
	    name: mega
	    collaborators: 60
	    space: 20971520
	    private_repos: 125

	
### Authenticated User Management ###

If you are authenticating, you can update your users information by POSTing to in a few different ways.

	  /user/show/:username [POST]

	      :values[key] = value

Where the POST values are of :

	name
	email
	blog
	company
	location

So, you could do this to update your email address:

	$ curl -F 'login=schacon' -F 'token=XXX' https://github.com/api/v2/json/user/show/schacon -F 'values[email]=scott@geemail.com'
	{
	  "user": {
	    "company": "Logical Awesome",
	    "name": "Scott Chacon",
	    "blog": "http:\/\/jointheconversation.org",
	    "disk_usage": 89352,
	    "collaborators": 3,
	    ...
	    "email": "scott@geemail.com",
	    "location": "Redwood City, CA"
	    "created_at": "2008\/01\/27 09:19:28 -0800",
	  }
	}


### Following Network ###

If you want to look at the following network on GitHub, you can request the users that a specific user is following with:

	/user/show/:user/followers

or the users following a specific user with:

	/user/show/:user/following

For example, if you want to see which users are following 'defunkt', you can run this:

	$ curl -i http://github.com/api/v2/yaml/user/show/defunkt/followers

If you are authenticated as a user, you can also follow or unfollow users with:

	/user/follow/:user [POST]

	/user/unfollow/:user [POST]


### Watched Repos ###

To see which repositories a user is watching, you can call:

	/repos/watched/:user

For example,

	$ curl http://github.com/api/v2/yaml/repos/watched/schacon 
	repositories: 
	- :watchers: 42
	  :owner: ddollar
	  :name: git-db
	  :description: CouchDB-based git server
	  :private: false
	  :url: http://github.com/ddollar/git-db
	  :open_issues: 0
	  :fork: false
	  :homepage: http://github.com/ddollar/git-db
	  :forks: 2
	- :watchers: 2
	  :owner: schacon
	  :name: git-db
	  :description: CouchDB-based git server
	  :private: false
	  :url: http://github.com/schacon/git-db
	  :open_issues: 0
	  :fork: true
	  :homepage: http://github.com/ddollar/git-db
	  :forks: 0

#### Public Key Management ####

	  /user/keys

	  /user/key/add [POST]
	      :title
	      :key

	  /user/key/remove [POST]
	      :id

#### Email Address Management ####

	  /user/emails [GET]

	  /user/email/add [POST]

	  /user/email/remove [POST]
