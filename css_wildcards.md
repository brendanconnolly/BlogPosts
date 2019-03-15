<center><img src="http://www.brendanconnolly.net/wp-content/uploads/2019/03/css-wildcards-sketch.png" alt="CSS WildCard Selectors Sketch" width="70%"/></center>

## Contains `*=`

```
<h5 itemprop="name">
    <a class="product-name" href="http://automationpractice.com/index.php?id_product=3&amp;controller=product" title="Printed Dress" itemprop="url">
        Printed Dress
    </a>
</h5>
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
To match on the end of a string `$=`. 

For a real world example from the [Association for Software Testing](https://www.associationforsoftwaretesting.org)
```
<ul id="top-menu" class="nav">
    <li id="menu-item-63669" class="menu-item menu-item-type-post_type 
    menu-item-object-page menu-item-has-children menu-item-63669">
    <a href="https://www.associationforsoftwaretesting.org/about/">About</a>
</ul>

```
In this particular case it may seem just as easy to match on the link text `About`. It would work, but it gives me pause. The text could be changed, it could be internationalized and tests may work in one locale but break in others. The url to the about page is more likely to remain unchanged, but who wants to include the full url in a selector.

The selector will match on the end of the route.
```
a[href$='about/']
```
and clicking that element: 
```ruby
page.find(".nav").find("a[href$='about/']")

```

## In List `~=`
Sometimes the element you are searching for has a value you want to use to locate it but it's not the only value assigned to the attribute. You often see this with the `class` attribute but it's not a problem because using the `.` selector will find a specific class in the list of assigned classes.

For a real world example from [Github](https://github.com/SeleniumHQ/selenium)

```
<a data-hotkey="g p" itemprop="url" class="js-selected-navigation-item reponav-item" 
  data-selected-links="repo_pulls checks /SeleniumHQ/selenium/pulls" href="/SeleniumHQ/selenium/pulls">
```

Looking at the `data-hotkey` attribute as an example, it may not seem that bad to use the full text to match on since it is so short and a hotkey seems unlikely to change. Not every attribute is so short and friendly though, I wouldn't want to try a full text match for `data-selected-links`.

Using `~=` will look for the value in a space separated list.  

The selector to find based on ` p ` value in `data-hotkey`:
```
a[data-hotkey~='p']
```
and clicking that element: 
```ruby
page.find("a[data-hotkey~='p']").click

```



