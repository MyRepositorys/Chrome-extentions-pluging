# CSDN 页面优化



```javascript
点击展开按钮
	document.querySelector('#btn-readmore').click();

删除左侧边栏
	document.querySelector('aside').remove();

删除右侧边栏
	document.querySelector('.tool-box,.vertical').remove();
	document.querySelector('.csdn-side-toolbar').remove();

删除顶部导航栏
	document.querySelector('#csdn-toolbar').remove();

删除底部推广：
	document.querySelector('.recommend-box').remove();

删除底部评论区：
	document.querySelector('.comment-box').remove();

删除底部推荐页：
	document.querySelector('.recommend-box').remove();

将页面主体放到'80%'
	document.querySelector('main').style.width='80%';




```





> ### 制作chrome 扩展插件

```json
新建一个名字是manifest.json的文件，这个文件是chrome扩展插件的入口，必须是这个名字
{
  "name": "My Extension",	// name 随便写
  "version": "0.1",			//version 是你写的插件的版本，随便写
  "manifest_version" : 2,	//这个是必须这样写的，指定mainfest的版本
  "description": "Does some simple stuff",	//这个是描述，随便写，
  "background" : {				//指定浏览器在后台要干的事情
    "scripts" : ["background.js"]	//指定浏览器要运行的脚本
  },
  "browser_action": {			//指定浏览器的行为
    "default_icon": "logo .png"，	//指定显示在URL地址栏后面扩展插件的logo
    "default_title":"xxx插件"			//指定当鼠标移到到扩展插件上显示的名字
  },
  "permissions": ["activeTab"]		//向浏览器申请不会导致警告的权限
}
```



```javascript
需求就是点击扩展插件图标，执行自定义js脚本，那么就需要在background.js中写入下列代码
chrome.browserAction.onClicked.addListener(function(tab) {
   chrome.tabs.executeScript(null, {file: "testScript.js"});
});
```



> ### 测试视频如下:

<img src='D:\Program Files(x86)\typora\gif\fuck_CSDN.gif'>







> 出现的问题

```json
由于该插件不是在chrome 插件商店下载的，所以每次使用都会警告，'请停用开发者模式运行的插件'
解决办法：
	有大佬写了一个补丁，下载之后放在chrome浏览器的安装目录中，点击运行，然后选择chrome目录下的chrome.dll，补丁就会执行，再次打开浏览器，就没有弹窗了
```

