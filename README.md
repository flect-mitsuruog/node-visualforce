Grunt Node Salesforce, enables Salesforce application development. 

Getting Started

This plugin requires Grunt ~0.4.2

If you haven't used Grunt before, be sure to check out the Getting Started guide, as it explains how to create a Gruntfile as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

npm install grunt-node-salesforce --save-dev

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

grunt.loadNpmTasks('grunt-node-salesforce');

Once you added the task to your Gruntfile, you have to put all your project files inside the following folder structure:

	- /input
		-> /pages 			    #put all your .html files here
		-> /staticresources     #static resources folder
			-> /css 			#put all your .css files here
			-> /js 				#put all your .js files here
			-> /img 			#put all your image files here
			-> /fonts 			#put all your fonts files here


Then, you can execute the following tasks from the command line:

	**************************************************************************************************************************
	grunt build

	- it creates the following /output folder structure
		- /output
			-> /pages 				 #visualforce page files will be here
			-> /staticresources   	 #static resources package will be here

	- it generates all the visualforce page files (and the corresponding metadata files) from the html files located on the /input/pages folder and put them on /output/pages.
	- it creates a static resource package (and the corresponding metadata file) from all the files located on the /staticresources subfolders and put it on /output/staticresources.

	### Build-Task options

	#### options.inputPaht
	Type: `String`
	Default value: `'input/'`
	This option sets the source folder where there´re the files to proccess

	#### options.outputPath
	Type: `String`
	Default value: `output/`
	output folder where the plugin create the *.page files and the static resource file to be deployed on

	#### options.staticResourceName
	Type: `String`
	Default value: `staticResources`
	static resource file name

	### Overview
	In your project's Gruntfile, add a section named `build` to the data object passed into `grunt.initConfig()`.

	```js
	grunt.initConfig({
	  build: {
	    options: {
	    	inputPath:'input/',
	    	outputPath:'output/',
	    	staticResourceName:'staticResources'
	    }
	  }
	});

	```

	**************************************************************************************************************************

	grunt deploy

	- it deploys all the generated visualforce pages (with metadata) and the static-resources package (with metadata) to the configured Salesforce Org.

	### Deploy-Task options

	#### options.user
	Type: `String`
	Required: `true`
	Your Salesforce.com username

	#### options.pass
	Type: `String`
	Required: `true`
	Your Salesforce.com password

	#### options.token
	Type: `String`
	Your Salesforce.com securitytoken

	#### options.serverurl
	Type: `String`
	Default value: `'https://login.salesforce.com'`
	This option sets login url

	#### options.apiVersion
	Type: `String`
	Default value: `'29.0'`
	This option sets the api version to use for the package deployment

	### Overview
	In your project's Gruntfile, add a section named `deploy` to the data object passed into `grunt.initConfig()`.

	```js
	grunt.initConfig({
	  deploy: {
	    your_target: {
	      options:{
	      	user:'myusername@test.com',
	        pass:      'mypassword',
	        token:     'mytoken',
	        serverurl: 'https://test.salesforce.com', // default => https://login.salesforce.com
	        apiVersion: '29.0'
	      },
	      // Target-specific file lists and/or options go here.
	      pkg: {   // Package to deploy
	        staticresource: ['*']
	      }
	    }
	  }
	})
	```

Release History

(Nothing yet)