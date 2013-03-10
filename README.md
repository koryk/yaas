yaas
====

'Y'ii 'A'lternative 'A'pplication 'S'tructure - a skeleton Yii framework application directory structure based on what is used for the Yiiframework.com site itself and outlined in the wiki article: http://www.yiiframework.com/wiki/155/the-directory-structure-of-the-yii-project-site

Directory Structure
-------------------
The main directory contains the following directories:

 - backend: a Yii Web application to hold non public-facing administrative functionality
 - frontend: the front-end Yii Web application - this represents your public-facing website
 - console: a Yii console application for your console and utility commands
 - common: a directory housing any code or configuration that is to be shared across two or more of the above applications

Please read: http://www.yiiframework.com/wiki/155/the-directory-structure-of-the-yii-project-site for more information on the directory struture

Quick Start
===========
Download Yaas
-------------
And unpack to a local directory of your choosing

Install Yii
-----------
Then clone the latest read-only master branch of yii framework into common/lib/yii/ directory
```
$ cd common/lib
$ git clone https://github.com/yiisoft/yii.git yii
```
or you can download the desired version of the framework and move the contents of framework/ over to
common/lib/yii. When completed, ensure that common/lib/yii/framework/yii.php exists.

Deploy command
--------------
By default, yaas comes with three environments:
* local
* develpment
* production

Configure your environments
---------------------------
/console/config/params.php contains the configuration for the deploy command.
```php
	'environments' => array(
		'local' => array(
			'alias' => array('loc'),
			'parameters' => ''
		),
```

Ensure web server has read + write access to the following directories:
-----------------------------------------------------------------------
backend/runtime/  
backend/www/assets/  
console/runtime/  
frontend/runtime/  
frontend/www/assets/

Configure git to ignore filemode changes:
-----------------------------------------
    $ git config core.filemode false

Setup Web Document Roots
------------------------
Ensure that /frontend/www/ is an application webroot and /backend/www/ is also a webroot. These represent the frontend (public-facing) and backend (admin) applications. If using Apache web-server, one approach would be to setup vhosts that point to these directories as webroots.
E.G. 
local.yaas.com -> frontend/www/ 
and 
local.admin.yaas.com -> backend/www 
This way, if you visit http://local.yaas.com in your browser, it will run the index.php entry script at frontend/www/index.php. And similarly for the backend admin site.

One Other Quick Config Change
-----------------------------
Now that you have your frontend hostname setup, change the frontend.url setting in common/config/params-local.php to to match your setting


TODO
----
- Build deploy command with 3 environments
 * local (for a local machine)
 * development (for a remote box in a development environment)
 * production (for production level)
- Create comment headers for current codebase (SiteController, etc.) 
- Create coding style guide https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md http://www.yiiframework.com/doc/guide/1.1/en/basics.convention#code
