#Heisenberg - Zeek Starter Theme

This is the Zeek Starter theme, based on <a href="http://underscores.me/">Underscores</a> and Foundation 5.5.1.

## How to get started
### Prerequisites
* Install <a href="https://nodejs.org/download/" title="Permalink to the Node.js website for download instructions">Node.js</a>
* Install <a href="http://sass-lang.com/install" title="Permalink to the Sass website for install instructions">Sass</a>
* Install Bower - from Terminal or Command Prompt run `npm install --g bower`
* Install Gulp.js - from Terminal or Command Prompt run `npm install --global gulp`

**Note: if you run into errors when using Terminal, you may have to use the sudo command to install Bower or Gulp.js. For instance, `sudo npm install -g bower`**

## Dependencies
### Bower
**Install Foundation using Bower.** We use Bower as our front end package manager. To get started, run `bower install` and all of the packages will be brought into the `.assets/components` directory. We overwrote the default `bower_components` directory in `.bowerrc`; all Bower files are sent to `./assets/components`.

### Gulp
The theme dependencies are listed in our `package.json` file. If you run `npm install`, all of the plugin dependencies will be installed into `node_modules`.

Using the `gulpfile.js` file, gulp will handle Sass compiling, vendor-prefixing, CSS/JS minification and browser reloading.  It will automate a lot of tedious tasks for us.  Magic!

**Important:**  you’ll need to change both the proxy string from `'heisenberg.dev/'` to your local URL and the container string from `'heisenberg'` to your project name.

Once you’ve adjusted the two strings, from Terminal or Command Prompt run `gulp`.  Gulp will watch your Sass files and will compile when a change is made.  Also, <a href="http://www.browsersync.io/docs/gulp/" title="BrowserSync documentation">BrowserSync</a> will run and inject new CSS after compilation and will reload the browser when your PHP files change.

**CSS/Sass Tasks** – gulp will compile a minified and non-minified CSS file for you.  The theme will enqueue the non-minified CSS file if `WP_DEBUG` is set to true in the `wp-config.php` file.  It’s generally a good practice to do so anyway when developing themes.

**JavaScript Tasks** - gulp will concatenate all of the JavaScript files located in `./assets/js` into a new file named `app.js`. It will also create a minified version of the file and place both files in the `./assets/dist/js` directory.  Feel free to create as many JS files as you'd like rather than one long one. Gulp also uses the JSLint plugin check for any JavaScript errors for you (code quality). Read about the project here http://www.jslint.com/help.html.

The theme will enqueue the non-minified JS file if `WP_DEBUG` is set to true in the `wp-config.php` file, similar to how the CSS is structured (see above).

**What's up with the 'dist' directory?** - the `./assets/dist` directory is where gulp will send prepared JS and CSS files. The logic behind this is simply a nice segregated place to send and enqueue our files generated by gulp (outputs). That way we can keep our inputs and outputs separated. If you're not a fan and want it to go somewhere else, just adjust the `gulp.dest()` paths in the `gulpfile.js` for the 'js' and 'styles' tasks. Be sure to adjust your enqueue path in `functions.php` as well.

## How to use the Foundation Sass files
Using the `_settings.scss` file, you can overwrite a Foundation default style before things get compiled, thereby making your final CSS lighter.  To do so, find the variable in the file, uncomment it, and set the value you desire.  The file is located in `./assets/sass`.

Be sure to check <a href="http://foundation.zurb.com/docs/using-sass.html" title="Zurb Foundation documentation on using Sass">Foundation’s docs on using Sass</a> and their mixins for custom control on styles.

## Assets architecture
```
assets/
	|- components/				# Bower files go here
	|
	|- dist/						# Gulp generated files enqueued by theme go here
	|	|
	|	|- css/
	|	|
	|	|	|- app.css 				# Our non-minified development CSS file
	|	|	|- app.min.css 			# Our minified production CSS file
	|
	|	|- js/
	|	|
	|	|	|- app.js 				# Our non-minified development JavaScript file
	|	|	|- app.min.js 			# Our minified production JavaScript file
	|
	|- img/						# Images
	|
	|- js/						# JavaScript files
	|
	|- sass/
	|	|
	|	|– base/ 				 # Base element custom styles such as type, buttons, colors, etc. (non-Foundation stuff)
	|	|   |– _buttons.scss     # Buttons
	|	|   |– _mixins.scss      # Starting mixin library
	|	|   |– _typography.scss  # Typography rules
	|	|   |– _variables.scss   # Forms  
	|	|   ...                  # Etc.
	|	|
	|	|– components/  		 # Element items that are a combination of base items
	|	|   |– _navigation.scss  # Navigation
	|	|   ...                  # Etc.
	|	|
	|	|
	|	|– sections/ 			 # Element items that make up large sections of the application
	|	|   |– _header.scss      # Header
	|	|   |– _footer.scss      # Footer
	|	|   |– _sidebar.scss     # Sidebar
	|	|   ...                  # Etc.
	|	|
	|	|– pages/ 				 # Page specific styles
	|	|   |– _front-page.scss  # Home specific styles
	|	|	|– _page.scss  		 # Page specific styles
	|	|   ...                  # Etc.
	|	|
	|	|
	|	|– _settings.scss 		 # Foundation settings file
	|	|- _shame.scss 			 # Temporary work arounds
	|	|– app.scss              # Primary Sass file
```
## WordPress files
Our starter theme follows the Codex Template Hierarchy as found on http://codex.wordpress.org/Template_Hierarchy.

Site Front Page 		-	`front-page.php`
