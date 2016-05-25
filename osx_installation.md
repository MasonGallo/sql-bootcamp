# OSX Installation

## Installing MySQL Server and a client

### If you have [homebrew](http://brew.sh/) installed:

- `brew install mysql`
- `mysql.server start`
- Download and install [sequel pro](https://github.com/sequelpro/sequelpro/releases/download/release-1.1.2/sequel-pro-1.1.2.dmg)

### If you don't have [homebrew](http://brew.sh/) or don't want to use it:

- Download and install [mysql](http://dev.mysql.com/get/Downloads/MySQL-5.7/mysql-5.7.12-osx10.11-x86_64.dmg)
- Accept all of the defaults in the installation and set your root password to `test` when it asks (don't ever do this on anything public-facing of course!)
- Download and install [sequel pro](https://github.com/sequelpro/sequelpro/releases/download/release-1.1.2/sequel-pro-1.1.2.dmg)

## Testing your installation

- Open Sequel Pro
- Click quick connect (if it isn't already showing)
- Click the `Socket` tab
- Make sure name says `localhost` and username says `root`
- If you set a root password during your install, enter that in password
- Click connect!

## Video walkthrough

A video walkthrough of the installation process is available [here](https://www.youtube.com/watch?v=aoMnggYTrDE)