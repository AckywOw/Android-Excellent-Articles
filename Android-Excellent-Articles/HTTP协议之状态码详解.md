HTTP协议之状态码详解
----------------
## 目录 ##
* [前言](#preface)
* [什么是HTTP状态码](#what)
* [状态码分类](#category)
* [常见的状态码](#Common)
* [1XX 信息性状态码](#1XX)
* [2XX 成功状态码](#2XX)
* [3XX 重定向状态码](#3XX)
* [4XX 客户端错误状态码](#4XX)
* [5XX 服务器错误状态码](#5XX)
* [204 No Content(没有内容)](#204)
* [206 Partial Content(部分内容)](#206)
* [301 Moved Permanently（永久移除)](#301)
* [400 Bad Request（坏请求)](#400)
* [403 Forbidden(禁止)](#403)
* [405 Method Not Allowed(不允许使用的方法)](#405)
* [411 Length Required（要求长度指示）](#411)
* [413 Request Entity Too Large（请求实体太大）](#413)
* [414 Request URI Too Long(请求URI太长)](#414)
* [500 Internal Server Error(内部服务器错误)](#500)
* [501 Not Implemented(未实现)](#501)
* [501 Not Implemented(未实现)](#501)
* [502 Bad Gateway（网关故障）](#502)
* [505 HTTP Version Not Supported(不支持的HTTP版本)](#505)

<a name="preface"/>
##  前言 ##
HTTP状态码，我都是现查现用。 我以前记得几个常用的状态码，比如200，302，304，404， 503。 一般来说我也只需要了解这些常用的状态码就可以了。  如果是做AJAX，REST,网络爬虫，机器人等程序。还是需要了解其他状态码。  本文我花了一个多月的时间把所有的状态码都总结了下，内容太多，看的时候麻烦耐心点了。

HTTP状态码的学习资料到处都有，但是都是理论上讲解。  本文介绍HTTP协议中的HTTP状态码（HTTP Status Code）， 会对大部分的状态码都进行了详细的实例讲解。

要了解状态码，应该在实例中去理解状态码的意义，否则看了也会忘记的。

用Fiddler工具可以查看HTTP Request和Response, 还可以方便地查看Response中的状态码， 如果不熟悉这个工具，可以先参考【[Fiddler教程](http://www.cnblogs.com/TankXiao/archive/2012/02/06/2337728.html)】

为了重现HTTP 状态码，本文会使用Fiddler Composer来创建“特殊的HTTP Request”.  可以参考【[Fiddler Composer创建和发送HTTP Request](http://www.cnblogs.com/TankXiao/archive/2012/12/25/2829709.html)】

<a name="what"/>
## 什么是HTTP状态码 ##
HTTP状态码的作用是：Web服务器用来告诉客户端，发生了什么事。

状态码位于HTTP Response 的第一行中，会返回一个”三位数字的状态码“和一个“状态消息”。 ”三位数字的状态码“便于程序进行处理， “状态消息”更便于人理解。 

如下图，  当客户端请求一个不存在的URL的时候， Web服务器会返回 “HTTP/1.1 404 Not Found” 告诉浏览器客户端。 服务器无法找到所请求的URL。

<a name="category"/>
## 状态码分类 ##

<a name="Common"/>
## 常见的状态码 ##

<a name="1XX"/>
## 1XX 信息性状态码 ##

<a name="2XX"/>
## 2XX 成功状态码 ##

<a name="3XX"/>
## 3XX 重定向状态码 ##

<a name="4XX"/>
## 4XX 客户端错误状态码 ##

<a name="5XX"/>
## 5XX 服务器错误状态码 ##

<a name="204"/>
## 204 No Content(没有内容) ##

<a name="206"/>
## 206 Partial Content(部分内容) ##

<a name="301"/>
## 301 Moved Permanently（永久移除) ##

<a name="400"/>
## 400 Bad Request（坏请求) ##

<a name="403"/>
## 403 Forbidden(禁止) ##

<a name="405"/>
## 405 Method Not Allowed(不允许使用的方法) ##

<a name="411"/>
## 411 Length Required（要求长度指示） ##

<a name="413"/>
## 413 Request Entity Too Large（请求实体太大） ##

<a name="414"/>
## 414 Request URI Too Long(请求URI太长) ##

<a name="500"/>
## 500 Internal Server Error(内部服务器错误) ##

<a name="501"/>
## 501 Not Implemented(未实现) ##

<a name="502"/>
## 502 Bad Gateway（网关故障） ##

<a name="505"/>
## 505 HTTP Version Not Supported(不支持的HTTP版本) ##

