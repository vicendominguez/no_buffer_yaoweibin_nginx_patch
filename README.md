no_buffer_yaoweibin_nginx_patch
===============================
UPDATE: nginx > 1.7.11 supports no_buffering.

There is a complete description of this [here](http://vicendominguez.blogspot.com.es/2014/10/avoiding-nginx-buffers-request-of-body.html).

##Summary

This is my fast adaptation of the yaoweibin's no_buffer patch to the new nginx releases.

Weibin Yao (yaoweibin) is a motu working in the tengine project: https://github.com/yaoweibin 

Tengine (https://github.com/alibaba/tengine) is a web server originated by Taobao, the largest e-commerce website in Asia. It is based on the Nginx HTTP server and has many advanced features. Tengine has proven to be very stable and efficient on some of the top 100 websites in the world, including taobao.com and tmall.com 

At the moment, it is not possible avoid the buffering in the POST requests in NGINX. If you are working uploading large files to a backend, you know i am meaning.

Tengine has a patch (yaoweibin?) to solve it and it appears as a feature in its webpage: http://tengine.taobao.org/

    * Sends unbuffered upload directly to HTTP and FastCGI backend servers, which saves disk I/Os.

There is a pending ticket to Nginx team requesting that: http://trac.nginx.org/nginx/ticket/251 but there is not ETA:
http://forum.nginx.org/read.php?2,253626,253705#msg-253705

Finally, i chose to adapt the yaoweibin's patches (http://yaoweibin.cn/patches/) to the 1.7.6 nginx version.

##New configuration options

The new options in the conf file are:

 * client_body_buffers
 * client_body_postpone_size
 * proxy_request_buffering
 * fastcgi_request_buffering

The description of this new options is in this tengine page: http://tengine.taobao.org/document/http_core.html
     
:)


## CentOS 6 RPM

There is a CentOS 6 RPM here: http://repo.enetres.net/repoview/nginx.html
