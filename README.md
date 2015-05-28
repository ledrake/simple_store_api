#<center>Simple Store</center>
##<center>(Project: simple_store_api)</center>

This is a simple example of creating API versioning with out the use of a gem.  The intent is to show how API versioning may be implemented in an existing Rails app with out the use of an API gem.

Here is the idea: You have an existing Rails app.  The powers that be, have determined that an API needs to be added to the app.

Now because we are *"clairvoyant"* and see the future we know there is going to be a Schema change after we deploy to production, which will __not__ be backwards compatible with the existing API, AKA the API version in production will be broken, angering untold numbers of fellow developers :(.

So, now you know the future, your job is: 

1. Add/Create an API on/for the existing application.

2. Fix the break.

3. Add/Create a second API utilizing the same data as the first  version of the API incorporating the Schema Change.

You can review the git log to see how I implemented the changes.

There are a couple of branches you may wish to take note of  notably build_v2_api and build_version_into_accept_header.  At the conclusion of build_v2_api the API access looks like the following: 

```HTML
http://localhost:3000/api/v1/products.json
http://localhost:3000/api/v2/products.json
```

At the conclusion of "build_version_into_accept_header" access to the API looks like this:

```BASH
curl -H 'Accept: application/vnd.example.v1' http://localhost:3000/api/products
curl -H 'Accept: application/vnd.example.v2' http://localhost:3000/api/products
```

If you wish to test this for yourself check out the branch you desire.

A final note.  This project was "generated", using Rails version 4.2.0 and Ruby version 2.2.0.  Yes that is correct it was generated from a BASH script!

The "BASH" script is in the genesis folder the script name is __gen_simple_store__.  Given that you may want to have a peek at the generator script I suggest that you start at line No. 799 and proceed down from there, to see the detail instructions/steps.  The individual methods/functions are all defined before line No. 799.

2015-05-28


