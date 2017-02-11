# A Docker Config for Laravel

It is what it says.  Minimal set of configs to get docker contains up and running.

## Another One?
### Before you ask

Yes, this is yet another "*Let's run Laravel in Docker*" repo.

No, this is not another "*THIS SHOULD BE THE OFFICIAL LARVEL DOCKER*" repo.
### Then Why
I spin up a lot of Laravel projects, and needed an easier way to copy the settings ***I*** need, in a lot of places.  

If this helps you, great.  If not, please check out [Laradock](https://github.com/laradock/laradock), [LaraEdit](https://github.com/laraedit/laraedit-docker), [one of the many others](https://github.com/search?q=laravel+docker), or roll your own.

## Configuration and Directories
### Configuration
A brief rundown on the hard-coded values in docker-compose.yaml.
* `nginx:volumes` and `php-fpm:volumes` both need to mount to the same location.
  * Due to link, php can't use `volumes_from:nginx` as it's a circular reference.
  * A 'data' container could be used to abstract volume definitions to a single source. [Stackoverflow Answer](http://stackoverflow.com/a/36187864).
* `nginx:environment:LARAVEL_PUBLIC` - Used to specify the path to the public folder.
* Current config assumes the folder structure as listed below.

### Directory Layout
The configuration is biased toward personal project layouts; this repo is installed next to Laravel, not within it.  Be sure to update the path to the public folder if you copy this repo elsewhere.

* Project Root Folder
  * docker (Directory) - from this repo
    * nginx
    * php
    * etc
  * docker-compose.yaml - from this repo
  * laravel
    * app
    * public
    * etc
  * etc
