#Below the fold JS
Lazily and asynchronously load CSS for "below the fold" files, and then replace the "above the fold" static CSS in head.

##How to use

Place your above the fold CSS content in a style element inside head. Ensure it has id="atf", and list your stylesheets in data-btf (separated by a semi-colon ;).

``` html

<head>
	<style id="atf" data-btf="style.css;third.css;">
		* {
			box-sizing: border-box;
		}
		html, body {
			height: 100%;
			font-family: Helvetica, Arial, sans-serif;
			margin: 0;
		}
		.first {
			height: 100%;
			background: black;
			color: white;
			padding: 40px 40px 20px;
		}
	</style>
</head>

```

Just before your body tag closes, asynchronously include btf.js.

``` html

	<script async src="btf.js"></script>
</body>

```

##What's going on?
Your browser will asynchrously load btf.js. Once this loads, it will iterate through your data-btf list of stylesheet URLs and asynchrously load and inject them into head.

Once this process has finished, your initial above the fold style element will be removed.