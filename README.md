# js加入收藏、设置为首页、收藏本页Collection

效果如下：
![](images/img.gif)

all code:
```
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
	<title>js代码制作点击设为首页和加入收藏功能</title>
	<meta name="description" content="js代码制作两个非常常用的网页特效，点击按钮设为首页、加入收藏、收藏本页功能。是网页制作必备的常用网页特效。" />
	<style>
		*{margin:0;padding:0;list-style-type:none;}
		a,img{border:0;}
		.demo{width:300px;margin:130px auto 0 auto;text-align:center;}
	</style>
</head>
<body>
<div class="demo">
	<a href="javascript:void(0);" id="setHomePage" onclick="SetHome(this)" style="behavior:url(#default#homepage);">
		<img src="images/sethome.gif" width="57" height="51" alt="设为首页" />
	</a>
	<a href="javascript:addToFavorite()">
		<img src="images/addfavorite.gif" width="57" height="51" alt="" />
	</a>
	<a href="javascript:AddFavorite(document.location.href,document.title);">
		<img src="images/share.jpg" width="57" height="51" alt="收藏本页" />
	</a>
</div>
</body>
</html>
<script>
	//收藏本页
	function AddFavorite(sURL, sTitle){
		try{
			window.external.addFavorite(sURL, sTitle);
		}
		catch(e){
			try{
				window.sidebar.addPanel(sTitle, sURL, "");
			}
			catch(e){
				alert("加入收藏失败，请使用Ctrl+D进行添加");
			}
		}
	}

	//收藏设置页面（首页）
	function addToFavorite(){
		var d="http://www.baidu.com/";
		var c="百度";
		if(document.all){
			window.external.AddFavorite(d,c);
		}else{
			if(window.sidebar){
				window.sidebar.addPanel(c,d,"");
			}else{
				alert("对不起，您的浏览器不支持此操作!\n请您使用菜单栏或Ctrl+D收藏本站。");
			}
		}
	}
	//设为首页
	function SetHome(obj){
		try{
			obj.style.behavior='url(#default#homepage)';
			obj.setHomePage('http://www.baidu.com/');
		}catch(e){
			if(window.netscape){
				try{
					netscape.security.PrivilegeManager.enablePrivilege("UniversalXPConnect");
				}catch(e){
					alert("抱歉，此操作被浏览器拒绝！\n\n请在浏览器地址栏输入“about:config”并回车然后将[signed.applets.codebase_principal_support]设置为'true'");
				}
			}else{
				alert("抱歉，您所使用的浏览器无法完成此操作。\n\n您需要手动将'http://www.baidu.com'设置为首页。");
			}
		}
	}
</script>


```

