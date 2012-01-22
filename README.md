# wget-gzip

This is a branch of GNU Wget that adds support for transparent HTTP compression. Wget will always send Accept-Encoding header in HTTP requests. If server returns Content-Encoding header the file is decompressed on the fly. 

## Standards

* Accept-Encoding request header per section 14.3 of RFC 2616
* Content-Encoding reply header per section 14.11 of RFC 2616
* Gzip compression per RFC 1952, using Zlib implementation

## Limitations

* Only "gzip" method is supported. 
* This is currently developed on Windows so it won't compile on Unix systms (not that it's impossible, it just needs some code clean up)