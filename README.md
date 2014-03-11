#Cooking steps
Assume you have some 3rd party project repository you want to work on. For some reasons it does not allow commiting development specific data into project. This repoository provides approach to 'wrap' external repository into your own development environment.

Approach assumes that you use Vagrant dev environment (with berkshelf plugin installed).

Approach assumes that bash shell is in path (for windows environment it is located in msysgit bin folder)

## Steps:
1. Define your project cooking recipes in env\cookbooks-project\current_project_setup\ . This may include setting up specific databases, users, plugins, packages etc.
2.  Define hints for development website in \env\data_bags\sites\ . This may include DNS entries. I propose using localhost catchers like *.lvh.me - saves some time.
3.  Define your dev environment settings in env\environments\ .  I provide my default setup for vagrant as an example
4.  Roles: env\roles\ : actually portions from original 'big' approach at https://github.com/Voronenko/chef-developer_bootstrap - instructions to install software bundles specific to your development stack. Note: make sure, that Berksfile and Cheffile in the project root match software packages required.
5.  Register project you want to wrap into .projmodules file.  Syntax of the file is identical to .gitmodules format. Difference it - that wrapped project is not installed as a git submodule, but as fully independent project. Note - you have way to work with multiple projects/sites on the same vagrant box, if needed.
6.  Initialize .projmodules  with running init.sh in the project root
7.  I often use local folder to keep set of files I need to overwrite in original solution to make it run on a vagrant (usually pathes, DB credentials, etc)
8.  Feel free to commit your IDE related configs to parent repository (for example, I commit core settings from JetBrains IDea dev environment. In this way I have the same settings regardless of PC I work on)



## Enjoy!
