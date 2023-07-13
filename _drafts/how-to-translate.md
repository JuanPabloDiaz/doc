---
layout: post
title: "How to Tanslate a Jekyll Page"
date: 2023-06-30
author: juan
categories: jekyll customize
tags: jekyll featured-img
# image: /assets/img/featured-posts/design.jpg
---

I am not sure how to do it on Jekyll but here is an example on how to do it on HTML and JS

```js
	<!DOCTYPE html>
	<html lang="en">
	<head>
	<meta charset="UTF-8">
	<title> Google Translater for Website </title>
	</head>
	<body>
	<h2>Your Web Page</h2>
	<p>Click on the dropdown button to translate.</p>
	<p>Translate this page:</p>

	<div id="google_translate_element"></div>
	<script type="text/javascript">
	function googleTranslateElementInit() {
	new google.translate.TranslateElement({pageLanguage: 'en'}, 'google_translate_element');
	}
	</script>

	<script type="text/javascript" src="//translate.google.com/translate_a/element.js?cb=googleTranslateElementInit"></script>

	<p>You can translate the content of this page by selecting a language in the select box.</p>
	</body>
	</html>
```
