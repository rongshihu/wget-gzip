# wget-gzip

This is a branch of GNU Wget that adds support for transparent HTTP compression. Wget will always send Accept-Encoding header in HTTP requests. If server returns Content-Encoding header the file is decompressed on the fly. 

## Standards

* Accept-Encoding request header per [section 14.3 of RFC 2616](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.3)
* Content-Encoding reply header per [section 14.11 of RFC 2616](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.11)
* Gzip compression per RFC 1952, using [Zlib](http://zlib.net/)

## Limitations

* Only "gzip" method is supported. 
* This is currently developed on Windows so it won't compile on Unix systms (not that it's impossible, it just needs some code clean up)
* Only supports GNU TLS and not OpenSSL
* Does not support NTLM authentication (because of no OpenSSL support)

## Building

I'm using Visual C/C++ 2008 with [Git Source Control Provider](http://gitscc.codeplex.com/), so I'm just pulling the solution directly from GitHub. There are two empy dirctories _lib_ and _include_ that need to be populated with external library files.

* External libraries to compile wget-gzip
	- [zlib-lib](http://gnuwin32.sourceforge.net/downlinks/zlib-lib-zip.php)
		- Copy _lib_ from the archive to project's _lib_ directory
		- Copy _include_ from the archite to project's _include_ directory
	- [gnutls](http://homes.esat.kuleuven.be/~nikos/gnutls-win32/)
		- Copy _lib_ from the archite to project's _lib_ directory
		- Copy _include_ from the archite to project's _include_ directory
* External runtime libraries (DLL) to run wget-gzip
	- _libgnutls-28.dll, libgmp-10.dll, libhogweed-2-1.dll, libnettle-4-3.dll, libp11-kit-0.dll_ from the _gnutls_ [gnutls](http://homes.esat.kuleuven.be/~nikos/gnutls-win32/) (same as above)
	- _zlib1.dll_ from [zlib-bin](http://gnuwin32.sourceforge.net/downlinks/zlib-bin-zip.php)
	- You need to place these in SYSTEM32 or in the same folder as _wget.exe_ binary
