Swiftly
*******

Swiftly is a client tool that you can use to upload objects to and download objects from your Cloud Files account. Swiftly manages the storage of large objects in Cloud Files. If you have a very large object (such as a virtual disk image file), Swiftly splits the file into smaller segments and then creates the large object manifest for you.
************************************************************************
For more information about Swiftly, see the following sites:

The Python package index page: https://pypi.python.org/pypi/swiftly/2.02
Swiftly documentation: http://gholt.github.io/swiftly/
Swiftly source code: https://github.com/gholt/swiftly
************************************************************************

Install Swiftly on Ubuntu 
*************************
These instructions were verified on a server built from a Rackspace Ubuntu 16.04 public image.

Invoke the following instructions from a bash shell on your server.

Update the apt-get database.

sudo apt-get update
Install the Python installer, pip, using apt-get.

sudo apt-get install python-pip
Install Swiftly using pip.

sudo pip install swiftly

Install Swiftly on CentOS
*************************
These instructions were verified on a server built from a Rackspace CentOS 6+ public image.

Invoke the following instructions from a bash shell on your server.

Install the Python installer, pip, using yum.

sudo yum install python-pip
If you get an error saying the package can’t be found, the EPEL repository needs to be enabled. For information on setting up the EPEL repository on your system, see Install EPEL and additional repositories on CentOS and Red Hat. When EPEL is enabled, run the install command for pip again.

Install swiftly using pip.

sudo pip install swiftly
**********************************************************

The swiftly conf:
**********************************************************
[/root/.swiftly.conf]

[swiftly]
auth_user = mycloudusernamehere
auth_key = myapikeyhere
auth_url = https://identity.api.rackspacecloud.com/v2.0
region = LON

Troubleshooting/pre-reqs:
**********************************************************
Installing Necessary Dependencies
To use swiftly you'll need to install some other stuff along with it.

# CentOS Systems
yum install python-devel gcc python-pip
pip install swiftly eventlet
 
# Debian / Ubuntu or other aptitude based OS 
apt-get install python-dev gcc python-pip
pip install swiftly eventlet
**********************************************************

Example usage:
***************
# swiftly get
<if you have containers, they will be listed>

# swiftly --verbose delete gallery --recursive --until-empty

This deletes with concurrent connections:
swiftly --eventlet --concurrency 100 delete CONTAINER --until-empty --recursive


