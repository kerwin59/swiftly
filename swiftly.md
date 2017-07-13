# Swiftly
<p>Swiftly is a client tool that you can use to upload objects to and download objects from your Cloud Files account. Swiftly manages the storage of large objects in Cloud Files. If you have a very large object (such as a virtual disk image file), Swiftly splits the file into smaller segments and then creates the large object manifest for you.</p>
<br>
For more information about Swiftly, see the following sites:<br>
The Python package index page: https://pypi.python.org/pypi/swiftly/2.02<br>
Swiftly documentation: http://gholt.github.io/swiftly/<br>
Swiftly source code: https://github.com/gholt/swiftly<br>
<br>

# Install Swiftly on Ubuntu 
These instructions were verified on a server built from a Rackspace Ubuntu 16.04 public image.<br>
Invoke the following instructions from a bash shell on your server.<br>

# Update the apt-get database.
sudo apt-get update<br>

# Install the Python installer, pip, using apt-get.
sudo apt-get install python-pip<br>

# Install Swiftly using pip.
sudo pip install swiftly<br>

# Install Swiftly on CentOS
These instructions were verified on a server built from a Rackspace CentOS 6+ public image.<br>

Invoke the following instructions from a bash shell on your server.<br>

# Install the Python installer, pip, using yum.
sudo yum install python-pip<br>
<p>If you get an error saying the package can’t be found, the EPEL repository needs to be enabled. For information on setting up the EPEL repository on your system, see Install EPEL and additional repositories on CentOS and Red Hat. When EPEL is enabled, run the install command for pip again.</p>

# Install swiftly using pip.
sudo pip install swiftly<br>

# The swiftly conf:
[/root/.swiftly.conf]<br>

[swiftly]<br>
auth_user = mycloudusernamehere<br>
auth_key = myapikeyhere<br>
auth_url = https://identity.api.rackspacecloud.com/v2.0<br>
region = LON<br>

# Troubleshooting/pre-reqs:
Installing Necessary Dependencies<br>
To use swiftly you'll need to install some other stuff along with it.<br>

# CentOS Systems
yum install python-devel gcc python-pip<br>
pip install swiftly eventlet<br>
 
# Debian / Ubuntu or other aptitude based OS 
apt-get install python-dev gcc python-pip<br>
pip install swiftly eventlet<br>

# Example usage:
swiftly get<br>
if you have containers, they will be listed<br>

swiftly --verbose delete gallery --recursive --until-empty<br>

This deletes with concurrent connections:<br>
swiftly --eventlet --concurrency 100 delete CONTAINER --until-empty --recursive<br>

Download all items in container to specfic path:<br>
swiftly get --all-objects DEEPKNOWLEDGE_STATIC -o /root/customer/<br>

Backup one website:<br>
swiftly -v put -h "Content-Type: application/x-gzip" -n -i /var/www/vhosts/mydomain.net Weekly_web/mydomain.net<br>

Grabbing Holland backups of the databases -using ServiceNet -looking for different -weekly *set up cron for this to work
swiftly -v --snet put -h "Content-Type: application/x-gzip" -d -i /var/lib/mysqlbackup/default/ Weekly_databases<br>

Streaming into Swiftly works ---Any other ways to do this? maybe ??scp/rsync/cp/mv/gunzip??:<br>
cd /path/to/backup; tar zc . | swiftly put -qextract-archive=tar.gz -i - container<br>

swiftly -v put -h "Content-Type: image/jpeg" -i ../PicturesFolder/ PicturesContainer<br>

# Put local file to your Cloud Files:
First make sure the container exists...or create it:I haven't found a way around this errors with "OSError: [Errno 2] No such file or directory: 'file_name.txt'"<br>
swiftly -v put -h "Content-Type: application/x-gzip" TestGzipBackups<br>
swiftly put -h "Content-Type: application/x-gzip" -i /root/date_mydomain.net.tar.gz TestGzipBackups/date_mydomain.tar.gz<br>

