HashYeah's arsenal
===

HashYeah web components developed independently

我在重构自己的博客网站时开发的一些基于HTML5的组件，帮助别人的同时希望以后有用。

Title-index(标题索引DIV组件)
---

![](title-index/Display.png)  

一款扁平化的标题-图像-简介Html5组件。

···html
	 <div class="title-index ti-noselect" onmousemove="ti_Select(this)" onmouseout="ti_SelectOff(this)">
		 <img class="ti-img" src="https://git-scm.com/images/logo@2x.png"></img>
		 <div class="ti-title font-xirod">git工具</div>
		 <div class="ti-em-select dis-hide">Get</div>
		 <div class="ti-context">Git是目前世界上最先进的分布式版本控制系统（没有之一）。</div>
	 </div>
···

使用场景:导航、下载

该组件有两种状态方案：
1.鼠标经过改变状态
2.鼠标点击改变状态

目前有两个版本 一个原生js版，一个Vue版

