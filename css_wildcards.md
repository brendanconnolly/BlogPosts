<center><img src="http://www.brendanconnolly.net/wp-content/uploads/2019/03/css-wildcards-sketch.png" alt="CSS WildCard Selectors Sketch" width="70%"/></center>

## Contains `*=`

```
<a class="product_img_link" href="http://automationpractice.com/index.php?id_product=3&amp;controller=product" 
   title="Printed Dress" itemprop="url">
    <img class="replace-2x img-responsive" src="http://automationpractice.com/img/p/8/8-home_default.jpg" 
     alt="Printed Dress" title="Printed Dress" itemprop="image" width="250" height="250">
</a>
```
```
.product-name[href*='3&']
```
```ruby
page.find("ul[class~='homefeatured']").find(".product-name[href*='3&']")
```
## Starts With `^=`

```
<input id="user_login_5c88a03ff2e3d" placeholder="Username" class="input" type="text" value="" name="log">
```
```
input[id^='user_login']
```
``` ruby
page.find("input[id^='user_login']").set('my_name_is')
```


## Ends With `$=`

```
<ul id="top-menu" class="nav">
    <li id="menu-item-63669" class="menu-item menu-item-type-post_type 
    menu-item-object-page menu-item-has-children menu-item-63669">
    <a href="https://www.associationforsoftwaretesting.org/about/">About</a>
</ul>

```


```
a[href$='about/']
```
```ruby
page.find(".nav").find("a[href$='about/']")

```

## In List `~=`

```
<a data-hotkey="g p" itemprop="url" class="js-selected-navigation-item reponav-item" 
  data-selected-links="repo_pulls checks /SeleniumHQ/selenium/pulls" href="/SeleniumHQ/selenium/pulls">
```
```
a[data-hotkey~='p']
```
```ruby
page.find("a[data-hotkey~='p']").click

```



