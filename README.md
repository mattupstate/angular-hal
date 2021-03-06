# angular-hal

[![Build Status](https://travis-ci.org/LuvDaSun/angular-hal.svg)](https://travis-ci.org/LuvDaSun/angular-hal)

## use it in your project!

Easy installation using bower
	
	bower install angular-hal


then, reference the js file in your html page

	<script src="/bower_components/angular-hal/angular-hal.js"></script>


You may use it like this:
	
	angular
	.module('app', ['angular-hal'])
	.run([
		'$rootScope'
		, '$window'
		, 'halClient'
		, function(
			$rootScope
			, $window
			, halClient
		) {
			var token = $window.sessionStorage.getItem('token');

			$rootScope.apiRoot = halClient.$get('https://api.example.com/', {
				authorization: token && 'Bearer ' + token + ''
			});
		
			$rootScope.$watch('apiRoot', function(apiRoot){
				$rootScope.authenticatedUser = apiRoot.$get('http://example.com/authenticated-user');
			});

		}
	])//run

stay tuned for more!


## compatibility

If you wish to use this service in old (ie) browsers, you may need to use the following polyfills:
- es5shim & es5sham, https://github.com/kriskowal/es5-shim, some parts of the service use es5 methods.
- xhr-polyfill, git://github.com/LuvDaSun/xhr-polyfill.git, if you want to make cross domain requests in ie8 / ie9.

