---
layout: post
title: Arrays in Arendelle
---


You may know my language [Arendelle](http://web.arendelle.org), This month we officially released the first version of it for Android, currently we’re developing the language for the rest of the platforms. 

There are things we’re adding to the language and one of them is “Arrays”, Array actually give the user many super powers and it’s a very necessary part of our language. However what you don’t know is it’s already coming with the language in our Android app. 

Actually I made Arendelle Language in the first place but everything about array other than it’s size command were Micha’s ideas. Soon there will be some chapters in [Arendelle Book](http://web.arendelle.org/book/) explaining array and some exercises about it but for now let’s just have a quick look at it.

If you’re an Arendelle developer you may have used it without even knowing it! Because like MATLAB and Octave every single space you create is an Array! Yes! Every single space you make is an array, So when you’re doing `@space` you’re actually reading the very first index of that space. So now you may ask then how you add more things to it? Simple! When you do this:



<!-- CLIFF HIGHLIGHTER 0.05 DEV GENERATED CODE BLOCK-->

<pre style="font-family: Menlo, Monaco, 'Courier 10 Pitch', Monospace;">
<span style="color: #D60073;">(</span><span style="color: #4E00FC;">&nbsp;space&nbsp;</span><span style="color: #D60073;">,</span>&nbsp;<span style="color: #6200A8;">4</span>&nbsp;<span style="color: #D60073;">)</span></pre>

<!-- CLIFF HIGHLIGHTER 0.05 DEV GENERATED CODE BLOCK-->



Arendelle makes a space as `[ 4 ]` so now if you fill the next index with this code:

<!-- CLIFF HIGHLIGHTER 0.05 DEV GENERATED CODE BLOCK-->

<pre style="font-family: Menlo, Monaco, 'Courier 10 Pitch', Monospace;">
<span style="color: #D60073;">(</span><span style="color: #4E00FC;">&nbsp;space</span><span style="color: #D60073;">[</span>&nbsp;<span style="color: #6200A8;">1</span>&nbsp;<span style="color: #D60073;">]</span>&nbsp;<span style="color: #D60073;">,</span>&nbsp;<span style="color: #6200A8;">12</span>&nbsp;<span style="color: #D60073;">)</span></pre>

<!-- CLIFF HIGHLIGHTER 0.05 DEV GENERATED CODE BLOCK-->

You will have `@space = [4, 12]`. Something very very cool about Micha’s implementation is if you do: 

<!-- CLIFF HIGHLIGHTER 0.05 DEV GENERATED CODE BLOCK-->

<pre style="font-family: Menlo, Monaco, 'Courier 10 Pitch', Monospace;">
<span style="color: #D60073;">(</span><span style="color: #4E00FC;">&nbsp;space</span><span style="color: #D60073;">[</span>&nbsp;<span style="color: #6200A8;">5</span>&nbsp;<span style="color: #D60073;">]</span>&nbsp;<span style="color: #D60073;">,</span>&nbsp;<span style="color: #6200A8;">2</span>&nbsp;<span style="color: #D60073;">)</span></pre>

<!-- CLIFF HIGHLIGHTER 0.05 DEV GENERATED CODE BLOCK-->

When it comes to other languages arrays are horrible, For example you have to create them with a limited size like when you do this in c:


```c
int array[4] = {1, 234, 232, 34};
```


Which is not that cool. In some other languages like Swift, C# and so there are mutable arrays with unlimited size witch you can append them whenever you want like this way in Swift:


```Swift
var array = [1, 234, 232]
array.append(34)
```


In Arendelle spaces are mutable and you can add to them whenever you want, However the very cool feature of these arrays is you can do this:

<!-- CLIFF HIGHLIGHTER 0.05 DEV GENERATED CODE BLOCK-->

<pre style="font-family: Menlo, Monaco, 'Courier 10 Pitch', Monospace;">
<span style="color: #D60073;">(</span><span style="color: #4E00FC;">&nbsp;space&nbsp;</span><span style="color: #D60073;">,</span>&nbsp;<span style="color: #6200A8;">24</span>&nbsp;<span style="color: #D60073;">)</span><br><span style="color: #D60073;">(</span><span style="color: #4E00FC;">&nbsp;space</span><span style="color: #D60073;">[</span>&nbsp;<span style="color: #6200A8;">4</span>&nbsp;<span style="color: #D60073;">]</span>&nbsp;<span style="color: #D60073;">,</span>&nbsp;<span style="color: #6200A8;">256</span>&nbsp;<span style="color: #D60073;">)</span></pre>

<!-- CLIFF HIGHLIGHTER 0.05 DEV GENERATED CODE BLOCK-->
So the cool part is when you init the `@space` with `24` it will be `[24]` as soon as you do `(space[ 4 ], 256)` you’re telling Arendelle to fill the fifth index, but as you know there is no second, third and fourth index and it’s no problem because Arendelle automatically fills these indexes with zero for you, So the result of the code will be `[24, 0, 0, 0, 256]`

One thing that remains is how you get the size of an array? It will be done using our ‘?’ operator. When you append the name of a space with `?` you’re asking it’s size, So for example if you do:

<pre class="arendelle">( space [ 9 ] , 5 )
'Size of @space is | @space? |'</pre>

You will get the title:

```
Size of @space is 10
```

So there are many possible uses of array and it’s tools. For a simple example let’s make a list of 10 random number less than 11:

<!-- CLIFF HIGHLIGHTER 0.05 DEV GENERATED CODE BLOCK-->

<pre style="font-family: Menlo, Monaco, 'Courier 10 Pitch', Monospace;">
<span style="color: #D60073;">(</span><span style="color: #4E00FC;">&nbsp;space&nbsp;</span><span style="color: #D60073;">,</span>&nbsp;<span style="color: #6200A8;">0</span>&nbsp;<span style="color: #D60073;">)</span>&nbsp;<span style="color: #D60073;">(</span><span style="color: #4E00FC;">&nbsp;array&nbsp;</span><span style="color: #D60073;">,</span>&nbsp;<span style="color: #6200A8;">0</span>&nbsp;<span style="color: #D60073;">)</span><br><span style="color: #D60073;">[</span>&nbsp;<span style="color: #6200A8;">20</span>&nbsp;<span style="color: #D60073;">,</span><br>&nbsp;&nbsp;&nbsp;<span style="color: #D60073;">(</span><span style="color: #4E00FC;">&nbsp;array</span><span style="color: #D60073;">[</span>&nbsp;<span style="color: #4E00FC;">@space</span>&nbsp;<span style="color: #D60073;">]</span>&nbsp;<span style="color: #D60073;">,</span>&nbsp;floor<span style="color: #D60073;">(</span>&nbsp;<span style="color: #4E00FC;">#rnd</span>&nbsp;*&nbsp;<span style="color: #6200A8;">11</span>&nbsp;<span style="color: #D60073;">)</span>&nbsp;<span style="color: #D60073;">)</span><br>&nbsp;&nbsp;&nbsp;<span style="color: #D60073;">(</span><span style="color: #4E00FC;">&nbsp;space&nbsp;</span><span style="color: #D60073;">,</span>&nbsp;+<span style="color: #6200A8;">1</span>&nbsp;<span style="color: #D60073;">)</span><br><span style="color: #D60073;">]</span></pre>

<!-- CLIFF HIGHLIGHTER 0.05 DEV GENERATED CODE BLOCK-->

You can do it in a very more small system with only one space like this:

<!-- CLIFF HIGHLIGHTER 0.05 DEV GENERATED CODE BLOCK-->

<pre style="font-family: Menlo, Monaco, 'Courier 10 Pitch', Monospace;">
<span style="color: #D60073;">(</span><span style="color: #4E00FC;">&nbsp;array&nbsp;</span><span style="color: #D60073;">,</span>&nbsp;<span style="color: #6200A8;">0</span>&nbsp;<span style="color: #D60073;">)</span>&nbsp;<span style="color: #D60073;">[</span>&nbsp;<span style="color: #6200A8;">20</span><span style="color: #D60073;">,</span>&nbsp;<span style="color: #D60073;">(</span><span style="color: #4E00FC;">&nbsp;array&nbsp;</span><span style="color: #D60073;">[</span>&nbsp;<span style="color: #4E00FC;">@array?</span>&nbsp;-&nbsp;<span style="color: #6200A8;">1</span>&nbsp;<span style="color: #D60073;">]</span>&nbsp;<span style="color: #D60073;">,</span>&nbsp;floor<span style="color: #D60073;">(</span>&nbsp;<span style="color: #4E00FC;">#rnd</span>&nbsp;*&nbsp;<span style="color: #6200A8;">1</span>&nbsp;<span style="color: #D60073;">)</span>&nbsp;<span style="color: #D60073;">)</span>&nbsp;<span style="color: #D60073;">]</span>&nbsp;</pre>

<!-- CLIFF HIGHLIGHTER 0.05 DEV GENERATED CODE BLOCK-->

So as you see it’s very simple in Arendelle, Also stored spaces and functions are working with this system. You can do:

<pre class="arendelle">( $space , 0 ) ( $space[ 9 ] , 1024 )
'Index 0 is: | $space |, Index 9 is: | $space[ 9 ] |, Size is: | $space? |'</pre>

And as you know Arendelle uses `@return` in functions for storing the return value so you can return multi values grouped in `@return` like:


<!-- CLIFF HIGHLIGHTER 0.05 DEV GENERATED CODE BLOCK-->

<pre style="font-family: Menlo, Monaco, 'Courier 10 Pitch', Monospace;">
<span style="color: #D60073;">!func</span><span style="color: #D60073;">(</span><span style="color: #D60073;">)</span><span style="color: #D60073;">[</span>&nbsp;<span style="color: #6200A8;">0</span>&nbsp;<span style="color: #D60073;">]</span>&nbsp;<span style="color: #A0A0A0;">//&nbsp;value&nbsp;1</span><br><span style="color: #D60073;">!func</span><span style="color: #D60073;">(</span><span style="color: #D60073;">)</span><span style="color: #D60073;">[</span>&nbsp;<span style="color: #6200A8;">1</span>&nbsp;<span style="color: #D60073;">]</span>&nbsp;<span style="color: #A0A0A0;">//&nbsp;value&nbsp;2</span><br></pre>

<!-- CLIFF HIGHLIGHTER 0.05 DEV GENERATED CODE BLOCK-->

<br><br>
<hr>
**NOTE**: To copy a space to another space *Fully as an array* you can simply do:

<!-- CLIFF HIGHLIGHTER 0.05 DEV GENERATED CODE BLOCK-->

<!-- CLIFF HIGHLIGHTER 0.05 DEV GENERATED CODE BLOCK-->

<pre style="font-family: Menlo, Monaco, 'Courier 10 Pitch', Monospace;">
<span style="color: #D60073;">(</span><span style="color: #4E00FC;">&nbsp;space2&nbsp;</span><span style="color: #D60073;">,</span>&nbsp;<span style="color: #4E00FC;">@space</span>&nbsp;<span style="color: #D60073;">)</span></pre>

<!-- CLIFF HIGHLIGHTER 0.05 DEV GENERATED CODE BLOCK-->


Arendelle won't do:

<!-- CLIFF HIGHLIGHTER 0.05 DEV GENERATED CODE BLOCK-->

<pre style="font-family: Menlo, Monaco, 'Courier 10 Pitch', Monospace;">
<span style="color: #D60073;">(</span><span style="color: #4E00FC;">&nbsp;space2</span><span style="color: #D60073;">[</span><span style="color: #6200A8;">0</span><span style="color: #D60073;">]</span>&nbsp;<span style="color: #D60073;">,</span>&nbsp;<span style="color: #4E00FC;">@space</span><span style="color: #D60073;">[</span><span style="color: #6200A8;">0</span><span style="color: #D60073;">]</span>&nbsp;<span style="color: #D60073;">)</span></pre>

<!-- CLIFF HIGHLIGHTER 0.05 DEV GENERATED CODE BLOCK-->

It will copy the whole `@space` to `@space2`
<hr><br><br>

So that’s it for now, There will be some more features added but before we officially launch it, You can have some fun with it!

