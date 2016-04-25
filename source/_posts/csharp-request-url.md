---
layout: post
title: ".net使用Request取得当前页面路径"
date: 2016-03-17 17:07:55 +0800
comments: true
categories: [C#,net] 
---

# .Net中使用Request对象取得路径的各方法!
	Request.Url.AbsoluteUri： http://4rkwt72tgs.proxy.qqbrowser.cc/WeChatSGYH/order_confirm.aspx?xcname=123&unid=30&xcid=3&xclength=9
	Request.Url.AbsolutePath: /WeChatSGYH/order_confirm.aspx
    Request.Url.Authority: 4rkwt72tgs.proxy.qqbrowser.cc
    Request.Url.DnsSafeHost: 4rkwt72tgs.proxy.qqbrowser.cc
    Request.Url.HostNameType: Dns
    Request.Url.LocalPath: /WeChatSGYH/order_confirm.aspx
    Request.Url.OriginalString: http://4rkwt72tgs.proxy.qqbrowser.cc:80/WeChatSGYH/order_confirm.aspx?xcname=123&unid=30&xcid=3&xclength=9
    Request.Url.PathAndQuery: /WeChatSGYH/order_confirm.aspx?xcname=123&unid=30&xcid=3&xclength=9