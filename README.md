# example-rest-not

This is a very simple webapp, to assist with travel planning
amongst the Southern Gulf Islands. The data supplied is old, so don't
rely on it for a current trip!

A model of the schedule is provided as an XML document, and encapsulated
with a CodeIgniter model. This webapp will be teased apart, so that the
schedule is managed "remotely", making way for potential multiple
clients to provide planning or booking front-end apps.

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

It also incorporates the Caboose package from the Jedi Academy.