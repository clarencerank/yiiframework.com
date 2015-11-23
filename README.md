yiiframework.com Website
========================

This project contains the source code for the yiiframework.com Website.

If you want to contribute please get in touch with us using the [issue tracker](https://github.com/yiisoft-contrib/yiiframework.com/issues). We will set up some contributions guidelines soon.


## INSTALLATION

Before you start, make sure you have installed [composer](https://getcomposer.org/) and [Node.js](http://nodejs.org/).
If you are on Debian or Ubuntu you might also want to install the [libnotify-bin](https://packages.debian.org/jessie/libnotify-bin) package, which is used by Gulp to inform you about its status.

```
# clone the project
git clone https://github.com/yiisoft-contrib/yiiframework.com.git

cd yiiframework.com

# install the composer asset plugin globally, if you haven't done so before
composer global require "fxp/composer-asset-plugin:~1.1.1"

# install the dependent composer packages
composer install

# install gulp globally if you haven't done so before
npm install -g gulp

# install browsersync globally if you haven't done so before
npm install -g browser-sync

# install dependent NPM modules
npm install

# initialize the application, choose "development"
./init

# build js/css files
gulp build

# The next step is for building the API documentation and the Guide files.
# It is optional for the site to be working but you will have no API docs and Guide.
# This step includes cloning the Yii 1 and Yii 2 repositories and a lot of computation,
# so you might want to skip it on the first install.
#
# This also requires an instance of elasticsearch to be configured and running
# (if you do not have it, it will still run, but the site search will not work).
# It also assumes you have pdflatex installed for building PDF guide docs.
#
# You may also build only parts of the docs, run  make help  for the available commands.
make docs


```


### Web Server Setup

Define a host name `local.yiiframework.com` that points to `localhost`.

Define a virtual host `local.yiiframework.com` which uses `yiiframework.com/web` as its document root.

If you are using Apache, add the following configuration for the `yiiframework.com/web` folder to hide the
entry script:

```
RewriteEngine on

# if a directory or a file exists, use it directly
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d

# otherwise forward it to index.php
RewriteRule . index.php
```


## DIRECTORY STRUCTURE

      commands/           contains console commands (controllers)
      config/             contains application configurations
      controllers/        contains Web controller classes
      data/               contains important data generated by different commands
      env/                contains environment-dependent files
      scss/               contains Sass source files
      mail/               contains view files for e-mails
      models/             contains model classes
      node_modules/       contains installed NPM packages
      runtime/            contains files generated during runtime
      js/                 contains JS source files
      scripts/            contains shell scripts
      vendor/             contains dependent 3rd-party packages
      views/              contains view files for the Web application
      web/                contains the entry script and Web resources


## DEVELOPMENT

### Build

* During development, run `gulp` to watch view, Sass and JS file changes and automatically build target CSS/JS files. This command will also launch a browser window which is connected to browsersync.
* At any time, run `gulp build` to manually rebuild target CSS/JS files from source Sass/JS files.
* If you only want to watch for changes, you can issue the command `gulp watch`

### CSS Files

* Use Sass files to define CSS styles.
* All Sass files should be put under `/scss` and listed in `/scss/all.scss`.
* Usually each controller corresponds to a single Sass file whose name is the same as the controller ID.
  For example, the `GuideController` has a Sass file named `_guide.scss`.
* All Sass source files, except `all.scss` should have a leading underscore in the name. Sass will ignore files starting with an underscore so that only one CSS file will be produced (all.css).


### JS Files

* All JS files should be put under `/js` and listed in `/js/all.json`.
* Usually each controller corresponds to a single JS file whose name is the same as the controller ID.
  For example, the `GuideController` has a JS file named `guide.js`.


## Links
* [Gulp](http://gulpjs.com/)
* [Browsersync](http://www.browsersync.io/)
* [Sass](http://sass-lang.com/)
