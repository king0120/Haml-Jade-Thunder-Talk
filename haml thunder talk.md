#Templating Languages
##Haml, Jade

Templating languages are used to beef up and organize your HTML code.  It makes writing html documents quick, easy, and clean.  Today I will be covering 2 of the most common options, Haml and Jade.


##Haml

Haml stands for HTML Abstraction Language and was created by Hampton Catlin in 2006.  (Fun fact, Hampton Catlin is also the creator of Sass!)

Haml is a replacement for erb.  It's syntax was built on the following principles.

 - Markup should be beautiful
 - Markup should be DRY
 - Markup should be well-indented
 - HTML structure should be clear

###Installation
 It's ridiculously easy to install haml.  Just install the gem with the following command.
 
 `gem install haml`

After you install haml, just use .haml at the end of your document name rather then .erb
 
###Syntax
Haml removes the need to close tags and use brackets in your html code.  

New tag:

`%strong= item.title`

this is the equivelant of 

`<strong><%= item.title %></strong>`

If you are just putting in static HTML, you write the same thing, but just minus the `=` sign.

`%h3 Hello, World!`

###Attributes
There are 3 ways to write out attributes in haml.  
`%a{:href => 'www.loremipsum.com', :class => 'links'}`

or just write out the class or id.  Haml will automatically wrapp a <div> tag around it.
`.you.can.even.put.in.multiple.classes.and#ids`

Alternatively, you can wrap the attributes in parenthesis and write your attributes in HTMLs normal syntax 
`%a(href='#' onclick='doSomething()')`

###Indentation
Haml and other templating engines uses strict indentation rules to compile correctly.  This means that everything in your file should be nested correctly.  If you indent with 3 spaces where you should have used 2, Haml will fail to compile and throw an error. 

%p This is an example.  <br>
  %p This will work.	<br>
   %p This will not work.
   
###Filters
The colon character tells haml to convert the indented block of text to a new language.  For example,
```
:css
	body{
		font-family: helvetica;
		color: green;
	}
```
This is useful for manipulating your css and javascript using your ruby code. Here are a few examples of available filters
 - :css
 - :erb
 - :javascript
 -	:markdown
 - :plain
 - :ruby
 - :sass
 - :scss

###Partials
Adding partials and combining multiple haml files is super easy.  all you have to do is include this in your file.

``` 
 = haml :file_name
```

You can combine this with other ruby code to cause certain conditions to call or ignore haml files.

###Other Syntax
`/` compiles into an HTML comment

`-#` is a Haml comment, and will not compile at all.

It is possible to pass through unmodified HTML tags.  


##Jade

Jade is a templating engine for Node and Javascript.  It is very similar to Haml's syntax.  Jade gives users the ability to use Javascript within their markup files.  An example of its usefulness can be found here.
```
- var authenticated = true
body(class=authenticated ? 'authed' : 'anon')
```

###	Case
Jade has it's own shorthand of the Javascript switch statement, that can be used to manipulate rendered HTML
```
- var quantity = 2
case quantity
	when 0
		p You have nothing in your cart
	when 1
	when 2
		p You don't have enough items in your cart!
	default
		p Thanks for shopping!
```
###Includes
You can include the contents of other files through this command.
```
	include ./folder/something.html
```

###String Interpolation
Jade borrows inline string interpolation from Ruby.  You can wrap a javascript expression between #{} to have it evaluate within the string.


###Shared with Haml
- Indentation
- Filters


###Examples
http://codepen.io/MyXoToD/pen/vdKsq?editors=110

http://codepen.io/katydecorah/pen/xADtE?editors=100