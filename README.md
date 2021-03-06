# example-ferries-standalone

This is a very simple webapp, to assist with travel planning
amongst the Southern Gulf Islands. The data supplied is old, so don't
rely on it for a current trip!

A model of the schedule is provided as an XML document, and encapsulated
with a CodeIgniter model. This webapp will be teased apart, as explained below.

This webapp is built on top of the CI3 starter3, and adds or changes the
following:

    /application
        /controllers
            Welcome.php
        /models
            Ferryschedule.php
        /views
            planner.php
            show_results.php
    /data
        ferryschedule.dtd
        ferryschedule.xml
    /public
        /assets
            ferry.png

It also incorporates the [Caboose package](https://github.com/jedi-academy/package-caboose), 
so that we can 
use the formfields helper; we don't need BootStrap or the Caboose library.

##Converting this standalone app into a distributed pair of apps

This app is a good candidate for teasing apart into distributed system components.
The ferry schedule data could be managed centrally, which would provide opportunities
for a number of client apps (for instance for different UI paradigms, or integrated
into business partners' websites). The client apps would share the same up-to-date
data, managed by the server app.

The most sensible solution, to me, is to modify our Ferryschedules model,
so that it makes remote requests to get data, rather than extracting it from
a local XML document.

Part of the problem with teasing this app apart is that two different techniques
apply, each to a different aspect of the app.
- accessing port data is very straightfoward, basically a subset of CRUD (that
would suit REST)
- accessing the sailing functionality is more of a remote procedure call (that
would suit XML-RPC)

There are two related repositories which demonstrate this:
- [example-ferries-server](https://github.com/jedi-academy/example-ferries-server), 
which has suitable endpoints for clients to access
port information and to request filtered sailing lists, and
- [example-ferries-client](https://github.com/jedi-academy/example-ferries-client), 
which uses appropriate distributed system glue to
make requests of the server.


##Deployment

This app is self-contained. Extract it somewhere suitable, and map
a virtual host (eg <code>alone.local</code>) to its <code>public</code> folder.
