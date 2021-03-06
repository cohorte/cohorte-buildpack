# A Cloud Foundry buildpack for Cohorte nodes
This buildpack should be used if you want to deploy a Cohorte Node on Cloud Foundry PaaS.

## Usage

````
cf push my_node -b https://github.com/cohorte/cohorte-buildpack.git
````

Your Cohorte  Node should have one directory *node* which contains your Cohorte node's artifacts :

`````
node\
|   |
|   |-- repo\              # your application bundles
|   |-- conf\              # configuration folder
|   |       | 
|   |       --- run.js     # startup configuration
|   |
|   |-- run                # startup executable
|
|-- manifest.yml           # cloud foundry manifest file
|-- runtime.txt            # (optional) version of python to instal
|-- requirements.txt       # (optional) other extra-python-dependencies to install
`````

*run.js* startup configuration file should specify Cohorte's runtime version to be installed (if not specified, the latest version is used).

`````
{ 
  "cohorte-version" : "1.0.0",
  "application-id"  : "my_app",
  "node-name"       : "led-raspberry"
  ...
}
````

If *runtime.txt* file is present, the specified Python version will be installed. Otherwise, this buildpack installs Python 3.4.0 by default.

If *requirements.txt* is present, this buildpack installs the specified dependencies.


