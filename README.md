# frab - conference management system

frab is a web-based conference planning and management system. 
It helps to collect submissions, to manage talks and speakers 
and to create a schedule.

## Background

frab was created for the organization of FrOSCon 2011 (http://www.froscon.de).
FrOSCon has previously used pentabarf (http://pentabarf.org), and although
frab is a completely new implementation, it borrows heavily from pentabarf.

Both FrOSCon and frab owe a lot to pentabarf. But sadly, pentabarf seems to
be abandoned. And several problems make it hard to maintain. Thus we decided
to create a new system.

## Current status

frab is under heavy development. There is no stable release yet.
You may want to try to use frab regardless, but be warned, that it may
be a rocky ride.

That being said, frab has been used to organize FrOSCon 2011, a
conference with more than 100 talks (and as many speakers) in more
than 5 parallel tracks (plus devrooms) over 2 days.

## Installing

frab is a pretty standard Ruby on Rails (version 3.1) application. 
There should be plenty of tutorials online on how to install,
deploy and setup these.

Basically, to get started you need git, ruby (>= 1.9.2) and bundler 
and follow these steps:

1) Clone the repository

    git clone git://github.com/oneiros/frab.git

2) cd into the directory:

    cd frab

3) Install all necessary gems:

    bundle install

4) Install Imagemagick:

This is a dependency of the paperclip gem. Imagemagick
tools need to be installed to identify and resize images.

Imagemagick should be easy to install using your OS's
preferred package manager (apt-get, yum, brew etc.).
 
5) Create (and possibly modify) the database configuration:

    cp config/database.yml.template config/database.yml

frab bundles all three built-in rails database drivers. 
And it should work with all three, although it is best tested 
with MySQL and SQLite3 (for development). 

6) Create and modify settings:

    cp config/settings.yml.template config/settings.yml

7) Create and setup the database

    rake db:setup

8) Precompile assets (only needed for production)

    rake assets:precompile

9) Start the server

To start frab in the development environment simply run

    rails server

To start frab in the production environment make sure you
did not skip step 8 and run:

    rails server -e production

(Note that for a "real" production environment you
probably do not want to use this script, but rather something
like unicorn or passenger.)

Navigate to http://localhost:3000/ and login as 
"admin@example.org" with password "test123".

## Migrating from pentabarf

frab comes with a script that offers limited capabilities of
migrating data from pentabarf. For it to work, you need access
to pentabarf's database and configure it in config/database.yml
under the key "pentabarf".

Then simply run

    rake pentabarf:import:all

Please note, that the script has not been tested with HEAD
and will most probably not work. If you still want to try it
out, checkout the code at the revision the script was last
changed at and upgrade the code and migrate the database
from there.

## License

frab is licensed under an MIT-License. It bundles some
third-party libraries and assets that might be licensed
differently. See LICENSE.
