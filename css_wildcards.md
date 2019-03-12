![ CSS WildCard Selectors Sketch](http://www.brendanconnolly.net/wp-content/uploads/2019/03/css-wildcards-sketch.png)

## Contains `*=`

## Starts With `^=`

## Ends With `$=`

```
<div class="code-buttons">
    <a class="btn btn-default" href="https://github.com/cypress-io/cypress">Check out the code</a>
</div>

```


```.code-buttons a[href$='/cypress']```

## In List `~=`

```
<a data-hotkey="g p" itemprop="url" class="js-selected-navigation-item reponav-item" data-selected-links="repo_pulls checks /SeleniumHQ/selenium/pulls" href="/SeleniumHQ/selenium/pulls">

a[data-hotkey=]
```





http://automationpractice.com/index.php

`
<a class="product_img_link" href="http://automationpractice.com/index.php?id_product=3&amp;controller=product" title="Printed Dress" itemprop="url">
							<img class="replace-2x img-responsive" src="http://automationpractice.com/img/p/8/8-home_default.jpg" alt="Printed Dress" title="Printed Dress" itemprop="image" width="250" height="250">
						</a>
`

page.find("a[href*='id_product=3']")

ul[class~='homefeatured']
.product-name[href*='3&']