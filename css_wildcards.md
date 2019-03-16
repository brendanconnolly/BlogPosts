<center><img src="http://www.brendanconnolly.net/wp-content/uploads/2019/03/css-wildcards-sketch.png" alt="CSS WildCard Selectors Sketch" width="70%"/></center>

Good selectors can be hard to find. It's always nice when the elements we need have automation friendly attributes, but sometimes thats not an option. These wildcards can help when you just need to match on part of what attributes are present. 

## Contains `*=`
There are times where finding a unique substring within a value is just the solution needed. In this case from the [Automation Practice](http://automationpractice.com/index.php) website, there are multiple products on a page all with the same markup and even the same text description. The link to the item though has the products unique id in it. 

Rather than use [string interpolation](https://en.wikipedia.org/wiki/String_interpolation) to generate the full link text, we can instead use `*=` to match just part of attributes value.
```
<h5 itemprop="name">
    <a class="product-name" href="http://automationpractice.com/index.php?id_product=3&amp;controller=product" title="Printed Dress" itemprop="url">
        Printed Dress
    </a>
</h5>
```
Using the class name in conjunction with `*=` to select the specific item on the page. 
```
.product-name[href*='3&']
```

The site has another section with the same item listed so the first find will narrow the scope of the search to the `homefeatured` section then look up our item and click on it.
```ruby
page.find("ul[class~='homefeatured']").find(".product-name[href*='3&']").click
```
## Starts With `^=`
Sometimes part of the attribute values you need are static but with dynamic or seemingly random data at the end. What seemed like a perfectly good and unique selector suddenly stops working the next time you run you tests or when new elements are added to the page.  For cases like this using `^=` will match on the beginning of the attributes value. 

For a real world example from [Ultimate QA's complicated page](https://www.ultimateqa.com/complicated-page/)

```
<input id="user_login_5c88a03ff2e3d" placeholder="Username" class="input" type="text" value="" name="log">
```
In this case the class attribute has some auto-generated value appended to the end of what otherwise would be a very easily located element.

Using `^=` with the selector to find based on `user_login`:
```
input[id^='user_login']
```

Then setting a value for that element: 
``` ruby
page.find("input[id^='user_login']").set('my_name_is')
```


## Ends With `$=`
Just like using `^=` to match on the beginning of a string, to match on the end of a string use `$=`.

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



