**version: 0.8**

**stability: 2 (rather stable)**

Charting Library package is available on GitHub. You may check out the latest stable version (`master` branch) or the most recent development build (`dev` branch). To have an access to this repo please contact us.

###Package content

	+/charting_library
		- charting_library.min.js
		- customization.txt
	+ /datafeed
	+ /udf
		- datafeed.js
	+ /static
	- index.html


* /charting_library contains all the library files
* /charting_library/charting_library.min.js contains an external Charting Library widget interface. This file is not supposed to be edited.
* /charting_library/customization.txt contains the description of customizable Widget properties
* /charting_library/datafeeds/udf/datafeed.js contains [UDF-compatible](UDF) datafeed wrapper (implements [JS API](JS-API) to connect to Charting Library and UDF to connect to datafeed) . Sample datafeed wrapper implement pulse realtime emulation. You are free to edit this file.
* /charting_library/static folder stores Charting Library internal content and is not intended for other purposes.
* /index.html is an example of using Charting Library widget on your web page
* /test.html is an example of different Charting Library customization features usage
* /mobile*.html also are examples of Widget customization

Starting from version 1.1, all internal Library's JS and CSS code is inlined & minified to reduce page load time. Files intended to be edited by you are not minified.
