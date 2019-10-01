# Treetracker Admin Panel

This portion of the project is to process tree data. TreeTracker's Admin Panel Frontend and RESTful API built with loopback.

See [Wiki](https://github.com/Greenstand/treetracker-admin-api/wiki) for more info on goals

### See [Current Milestone](https://github.com/Greenstand/treetracker-admin/issues?q=is%3Aopen+is%3Aissue+milestone%3A1.1.0)

See [Contributing to The Cause](https://github.com/Greenstand/Development-Overview#contributing-to-the-cause)

Please add any missing content to this readme.

## Setup

- Install Node
- on OSX , install git and type `brew install git`
- on OSX, install [home brew](http://brew.sh/) and type `brew install node`
- on Windows, use the installer available at [nodejs.org](http://nodejs.org/)
- On OSX you can alleviate the need to run as sudo by [following John Papa's instructions](http://jpapa.me/nomoresudo)
- Open terminal
- Go to a folder where you would like to install the project. Then type the following:
```bash
git clone https://github.com/Greenstand/treetracker-admin.git
```
- Once cloned type:
```bash
cd treetracker-admin/server && touch src/datasources/treetracker.datasource.json && npm install
```

- In `server/src/datasources/` directory you will need to create a `treetracker.datasource.json` file that will be used to reference the source of data for Loopback.

- **Contact the #admin-panel channel** on Slack to get our shared treetracker.datasource.json.


## Development Environment Quick Start

We provide a development environment through docker that can run on your local environment.

### Set Up Docker
To run docker on a local machine, you will have to install Docker first. Docker is a linux container technology, so running it on Mac or Windows requires an application with an attached linux VM. Docker provides one for each OS by default.

#### Mac
Install Docker for Mac using homebrew, using the following command

```
$ brew cask install docker
```

You can alternatively install Docker via:  [Docker for Mac] (https://docs.docker.com/docker-for-mac/install/)

Once Docker is installed, lauch Docker from the Applications GUI.

#### Windows

For most versions of Windows: [Docker for Windows](https://docs.docker.com/docker-for-windows/install/)
For some older versions or Win10 Home: [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/). At least on one machine, to get this to work, when you get to the step to do QuickStart terminal script, instead, run:
```
docker-machine create default --virtualbox-no-vtx-check
```
then re-run the QuickStart terminal script.

#### Linux

To install on linux, you can run `sudo apt-get install -y docker-ce` but there is [additional setup](https://docs.docker.com/install/linux/docker-ce/ubuntu/#set-up-the-repository) to verify keys, etc.


### Install, build docker containers and go

Install Node (see Requirements above)

Clone this repository

```
git clone git@github.com:Greenstand/treetracker-admin.git
cd treetracker-admin
```

Run the setup script.  This script installs node modules, builds docker containers, and starts them
```
./dev/scripts/setup.sh
```


You can now view the treetracker admin at http://localhost:8080.

*note: If you try to access the site on port 3001 you will recieve a CORS error* 

It may take a few seconds for the web and api servers to come up.  You can monitor them using the docker logs commands as:

```
docker logs -f treetracker-admin-web
docker logs -f treetracker-admin-api

Also see *Scripts* below
```

The REST API documentation can be viewed and explored by visiting http://localhost:3000/explorer


To stop the dev environment use

```
./dev/scripts/down.sh
```

To start the dev environment back up use

```
./dev/scripts/up.sh
```


Just edit as you normally would to view changes in your development environment.


### Alternative setup for MS Windows (Works on Linux and Mac also)
On Windows the easiest way to develop and debug Node.js applications is using Visual Studio Code.
It comes with Node.js support out of the box.

https://code.visualstudio.com/docs




## Quick Start For API only development

Run the following command to start the REST API.

```
$ npm run start
```

Run the following command to run the linter.

```
$ npm run lint
```

### Scripts

Useful scripts are contained in /dev/scripts.  Their uses are described here.  Scripts are run from the repository root as /dev/scripts/{script-name}.sh

**install.sh** install or update npm modules for server and client projects

**build.sh** build docker images

**up.sh** bring up docker containers in docker as described by docker-compose.yml

**setup.sh** run install.sh, build.sh, and up.sh

**down.sh** bring down docker containers

**logs-api.sh** show logs for api server

**logs-web.sh** show logs for React.js dev server

**docker-clear-images.sh** clear out *all* docker images

**docker-remove-containers.sh** clear out *all* docker containers


## Code style guide  

**Indention** 2 Spaces for indentation

**Semicolon** Use semicolons at the end of each line 

**Characters** 80 characters per line

**Quotes** Use single quotes unless you are writing JSON 

```
const foo = ‘bar’;
```

**Braces** Opening braces go on the same line as the statment 

```
If (true) {
	console.log(‘here’);
}
```

**Variable declaration** Declare one Varable per statment

```
const  dog = [‘bark’,’woof’];
let cat = [‘meow’,’sleep’]; 
```

**Variable, properties and function names** Use lowerCamelCase for variables, properties and function names

```
const adminUser =  db.query(‘SELECT * From users …’)
```

**Class names** Use UpperCamelCase for class names

```
class Dog {
	bark(){
		console.log(‘woof’);
	}
} 
```

**Descriptive conditions** Make sure to to have a descriptive name that tells the use and meaning of the code

```
const  IsValidPassword = password.length >= 4 && /^(?=.*\d).{4,}$/.test(password);
```

**Object/Array creation** Use trailing commas and put short declarations on a single line. Only quote keys when your interpreter complains:

```
var a = ['hello', 'world'];
var b = {
	good: 'code',
	'is generally': 'pretty',
};
```

## Credit
-----------
- [Loopback](https://loopback.io/doc/en/lb3/index.html)

