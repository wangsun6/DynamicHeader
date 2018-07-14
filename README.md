# Dynamic Header

If you are using javacscript for defining the logic for website without using PHP(assuming you don't know php functions and all). Then you might have encounter the problem of inserting same template in many pages like header and footer.
The big problen comes when you need to change the content, then you have to open every pages and edit them.

We all know it's very hard to make template in javascript, that's why we use php to make template and include them in different pages.

But wait, what if we want  them to change dynamically with respect to different pages.
One of the most commonly used template is Header and Footer. Footer we do not need dynamic change normally but what about Header?

We need some kind of Different style for home menu if we are in home page, and change the style when we are in about page.

We might have different solutions for them, but let's see one of the simple solution here:
You have to know 2 things about PHP, don't worry it's not related to programming. Then we will use our logic in javascript language. 
#### 1: to write php code in html you have to save the file in .php extension.
#### 2: to include template just write include and file name - 
```php
<?php include 'header.php'; ?>
```

In our example we will use same header template fore 3 pages(index/about/services). But at the same time we change the color of menu item to green, base on the page we visit.

### Header Template

```html
<header>
   <nav>
      <ul>
          <li id="menu_home"><a href="index.php">Home</a></li>
          <li id="menu_about"><a href="about.php">ABOUT</a></li>
          <li id="menu_services"><a href="services.php">SERVICES</a></li>
      </ul>
  </nav>
</header>

<script>
    document.getElementById(selected_menu).classList.add("active");
</script>
```

this is header template, here the important point is we have added different 'id' for each list item. Don't bother about script now.

### Body of HOME/index Page

```html
<body>
	
<script>
var  selected_menu="menu_home";
</script>

<?php include 'header.php'; ?>

<section class="showcase">
	<h1>This is Home Page</h1>
</section>

<?php include 'footer.php'; ?>
</body>
```

Here before including Header we have assigned selected_menu="menu_home", which is the id for list item 'home'.
After this we included the header. Now see the script we have added in header which will be common for all pages(that's why added in header itself).

```javascript
<script>
    document.getElementById(selected_menu).classList.add("active");
</script>
```

this will add the class 'active'(where we defined the style for selected item) to particular list item.

#### That's all, now you have dynamic template which changes it's style base on defferent pages.
