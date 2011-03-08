LocalFileSystem
==========

This interface supplies a way in which a file system entry point can be obtained.

Methods
----------

- __requestFileSystem:__ Requests a filesystem in which to store application data. _(Function)_
- __resolveLocalFileSystemURI:__ Allows the user to look up the Entry for a file or directory referred to by a local URI. _(Function)_

Constants
---------

- `LocalFileSystem.PERSISTENT`: Used for storage that should not be removed by the user agent without application or user permission.
- `LocalFileSystem.TEMPORARY`: Used for storage with no guarantee of persistence.

Details
-------

The `LocalFileSystem` objects methods are installed into the Window object so users can call the methods to line up with W3C specs.

Supported Platforms
-------------------

- Android
- BlackBerry WebWorks (OS 5.0 and higher)

Request File System Quick Example
-------------

	function onSuccess(fileSystem) {
		console.log(fileSystem.name);
	}
	
	// request the persistent file system
	window.requestFileSystem(LocalFileSystem.PERSISTENT, 0, onSuccess, onError);

Resolve Local File System URI Quick Example
-------------

	function onSuccess(fileEntry) {
		console.log(fileEntry.name);
	}

	window.resolveLocalFileSystemURI("file:///example.txt", onSuccess, onError);
	
Full Example
------------


    <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
                          "http://www.w3.org/TR/html4/strict.dtd">
    <html>
      <head>
        <title>Local File System Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // Wait for PhoneGap to load
        //
        function onLoad() {
            document.addEventListener("deviceready", onDeviceReady, false);
        }

        // PhoneGap is ready
        //
        function onDeviceReady() {
			window.requestFileSystem(LocalFileSystem.PERSISTENT, 0, onFileSystemSuccess, fail);
			window.resolveLocalFileSystemURI("file:///example.txt", onResolveSuccess, fail);
        }

		function onFileSystemSuccess(fileSystem) {
			console.log(fileSystem.name);
		}

		function onResolveSuccess(fileEntry) {
			console.log(fileEntry.name);
		}
		
		function fail(evt) {
			console.log(evt.target.error.code);
		}
		
        </script>
      </head>
      <body onload="onLoad()">
        <h1>Example</h1>
        <p>Local File System</p>
      </body>
    </html>