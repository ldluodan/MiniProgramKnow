
```
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
		<script type="text/javascript" src="js/jquery.js" ></script>
	</head>
	<body>
		<button id="getCode" type="button">获取短信验证码</button>
		<script>
			//获取短信验证码1
			var wait=60;
			function time(o) {
				if (wait == 0) {
						o.removeAttribute("disabled");
						o.innerHTML="获取动态码";
						wait = 60;
					} else {
						o.setAttribute("disabled", true);
						o.innerHTML="重新发送(" + wait + ")s";
						wait--;
					setTimeout(function() { time(o) }, 1000) 
				}
			}
			
			//"获取短信验证码2" 
			$('#getCode').unbind('click').click(function (event){
				event.preventDefault();
				time(this);
			});
		</script>
	</body>
</html>

```
