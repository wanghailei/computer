





```html
<details>
    <summary>The text shown</summary>
    The text hidden by default, and shown when the summary text is clicked.
</details>
```



### Input with a list of data options

```html
<input type="text" list="options">
<datalist id="options">
	<option value="Daily"></option>
	<option value="Weekly"></option>
	<option value="Monthly"></option>
</datalist>
```

### Input of date selector

```html
<input type="date">
```

### Input group of Username and Password

```html
<div class="d">
	<label for="email_input">Email</label><input type="email" id="email_input">
	<label for="password_input">Password</label><input type="password" id="password_input">
</div>
```





The <figure> element is meant to enclose media content—like images, charts, illustrations, or code snippets—along with an optional <figcaption> that describes it. Its purpose is to provide semantic structure, indicating that the media is a self-contained, referenced element within the content, distinct from inline or decorative visuals.





## Why is the "figure" necessary to exist?

It’s not strictly necessary but is certainly valuable for enhancing structure, meaning, and accessibility in HTML documents.

**Independent Flow**: <figure> elements can be placed within the main content or floated to the side without affecting the flow of the main text. This makes it easy to design layouts where figures act like floating blocks, adding visual separation between the main content and the supplementary media.

Semantic Clarity**: By marking up media with <figure>, HTML structure becomes more meaningful to both humans and search engines, screen readers and other accessibility tools. This can improve how content is indexed or displayed in search results.



**Study HTML**



我要設計開發一個 Appshell，用於製作 Business Applications。它要具備三個版本：電腦、平板、手機，其中電腦版優先。



三種佈局：



是否用 Side Menu？是否用 Mega Menu？





基礎顏色：白色、灰色、黑色

特殊顏色：紅色、綠色、藍色等。**HTML 5**





**For Structuring**



If the contents of the element represent a standalone, atomic unit of content that makes sense syndicated as a standalone piece (e.g. a blog post or blog comment, or a newspaper article), the <article> element would be a better choice.



If the contents represent useful tangential information that works alongside the main content, but is not directly part of it (like related links, or an author bio), use an <aside>.



If the contents represent the main content area of a document, use <main>.



If you are only using the element as a styling wrapper, use a <div> instead.





**<nav>**



The <nav> HTML element represents a section of a page whose purpose is to provide navigation links, either within the current document or to other documents. Common examples of navigation sections are menus, tables of contents, and indexes.



Notice that NOT all links of a document should be inside a <nav> element. The <nav> element is intended only for major blocks of navigation links.



Browsers, such as screen readers for disabled users, can use this element to determine whether to omit the initial rendering of this content.





**<menu>**



The <menu> HTML element is described in the HTML specification as a semantic alternative to <ul>, but treated by browsers (and exposed through the accessibility tree) as no different than <ul>. It represents an unordered list of items (which are represented by <li> elements).



<menu>

​	<li><button id="save">Save for later</button></li>

​	<li><button id="share">Share this news</button></li>

</menu>





**<main>**



The <main> tag specifies the main content of a document.

The content inside the <main> element should be unique to the document. It should not contain any content that is repeated across documents such as sidebars, navigation links, copyright information, site logos, and search forms.

Note: There must not be more than one <main> element in a document. The <main> element must NOT be a descendant of an <article>, <aside>, <footer>, <header>, or <nav> element.





**<section>**



The <section> HTML element represents a generic standalone section of a document, which doesn't have a more specific semantic element to represent it. Sections should always have a heading, with very few exceptions.



To reiterate, each <section> should be identified, typically by including a heading (h1 - h6 element) as a child of the <section> element, wherever possible. Circumstances where you might see <section> used without a heading are typically found in web application/UI sections rather than in traditional document structures.



<section>

<h2>WWF History</h2>

<p>The World Wide Fund for Nature (WWF) is an international organization working on issues regarding the conservation, research and restoration of the environment, formerly named the World Wildlife Fund. WWF was founded in 1961.</p>

</section>





**<aside>**



The <aside> HTML element represents a portion of a document whose content is only indirectly related to the document's main content. Asides are frequently presented as sidebars or call-out boxes.





**<article>**



The <article> tag specifies independent, self-contained content.

An article should make sense on its own and it should be possible to distribute it independently from the rest of the site.

Potential sources for the <article> element:Forum post, Blog post, News story



Note: The <article> element does not render as anything special in a browser. However, you can use CSS to style the <article> element (see example below).

<article>

​	<h2>Google Chrome</h2>

	<p>Google Chrome is a web browser developed by Google, released in 2008. Chrome is the world's most popular web browser today!</p>

</article>





**<footer>**



The <footer> tag defines a footer for a document or section. You can have several <footer> elements in one document.



A <footer> element typically contains: authorship information, copyright information, contact information, sitemap, back to top links, related documents.



<footer>

	<p>Author: Hege Refsnes</p>

  <p><a href="mailto:hege@example.com">hege@example.com</a></p>

</footer>





**<header>**



The <header> element represents a container for introductory content or a set of navigational links.



A <header> element typically contains: one or more heading elements (<h1> - <h6>), logo or icon, 

authorship information.



Note: You can have several <header> elements in one HTML document. However, <header> cannot be placed within a <footer>, <address> or another <header> element.



<article>

​	<header>

​		<h1>A heading here</h1>

		<p>Posted by John Doe</p>

		<p>Some additional information here</p>

​	</header>

	<p>Lorem Ipsum dolor set amet....</p>

</article>





**<search>**



The <search> HTML element is a container representing the parts of the document or application with form controls or other content related to performing a search or filtering operation. The <search> element semantically identifies the purpose of the element's contents as having search or filtering capabilities. The search or filtering functionality can be for the website or application, the current web page or document, or the entire Internet or subsection thereof.



The <search> is a semantic container for the <form> that submits the user-entered search query to a server.



<header>

​	<search>

​		<form action="./search/">

​			<label for="movie">Find a Movie</label>

​			<input type="search" id="movie" name="q" />

​			<button type="submit">Search</button>

​		</form>

​	</search>

</header>





**<input>**



The <input> tag specifies an input field where the user can enter data.

The <input> element is the most important form element.

The <input> element can be displayed in several ways, depending on the type attribute.

The different input types are as follows:

<input type="button">

<input type="checkbox">

<input type="color">

<input type="date">

<input type="datetime-local">

<input type="email">

<input type="file">

<input type="hidden">

<input type="image">

<input type="month">

<input type="number">

<input type="password">

<input type="radio">

<input type="range">

<input type="reset">

<input type="search">

<input type="submit">

<input type="tel">

<input type="text"> (default value)

<input type="time">

<input type="url">

<input type="week">

Look at the type attribute to see examples for each input type!



Tips and Notes

Tip: Always use the <label> tag to define labels for <input type="text">, <input type="checkbox">, <input type="radio">, <input type="file">, and <input type="password">.



<form action="/action_page.php">

 <label for="fname">First name:</label>

 <input type="text" id="fname" name="fname"><br><br>

 <label for="lname">Last name:</label>

 <input type="text" id="lname" name="lname"><br><br>

 <input type="submit" value="Submit">

</form>



**<button>**



The <button> tag defines a clickable button. Always specify the type attribute for a <button> element, to tell browsers what type of button it is.



Inside a <button> element you can put text (and tags like <i>, <b>, <strong>, <br>, <img>, etc.). That is not possible with a button created with the <input> element!



<button type="button">Click Me!</button>





**<mark>**



The <mark> tag defines text that should be marked or highlighted.





**<meter>**



The <meter> tag defines a scalar measurement within a known range, or a fractional value. This is also known as a gauge.

Examples: Disk usage, the relevance of a query result, etc.

Note: The <meter> tag should not be used to indicate progress (as in a progress bar). For progress bars, use the <progress> tag.

Tip: Always add the <label> tag for best accessibility practices!





**<data>**



The <data> tag is used to add a machine-readable translation of a given content. This element provides both a machine-readable value for data processors, and a human-readable value for rendering in a browser.



<ul>

​	<li><data value="21053">Cherry Tomato</data></li>

​	<li><data value="21054">Beef Tomato</data></li>

​	<li><data value="21055">Snack Tomato</data></li>

</ul>





**<datalist>**



The <datalist> tag specifies a list of pre-defined options for an <input> element.

The <datalist> tag is used to provide an "autocomplete" feature for <input> elements. Users will see a drop-down list of pre-defined options as they input data.

The <datalist> element's id attribute must be equal to the <input> element's list attribute (this binds them together).



<label for="browser">Choose your browser from the list:</label>

<input list="browsers" name="browser" id="browser">

<datalist id="browsers">

​	<option value="Edge">

​	<option value="Firefox">

​	<option value="Chrome">

​	<option value="Opera">

​	<option value="Safari">

</datalist>



**<object>**



The <object> tag defines a container for an external resource.

The external resource can be a web page, a picture, a media player, or a plug-in application.



**<param>**



The <param> tag is used to define parameters for an <object> element.



<object data="horse.wav">

​	<param name="autoplay" value="true">

</object>





**<optgroup>**



The <optgroup> tag is used to group related options in a <select> element (drop-down list).

If you have a long list of options, groups of related options are easier to handle for a user.





**<output>**



The <output> tag is used to represent the result of a calculation (like one performed by a script).



<form oninput="x.value=parseInt(a.value)+parseInt(b.value)">

​	<input type="range" id="a" value="50"> + <input type="number" id="b" value="25"> = 

​	<output name="x" for="a b"></output>

</form>





**<picture>**



The <picture> tag gives web developers more flexibility in specifying image resources.



The most common use of the <picture> element will be for art direction in responsive designs. Instead of having one image that is scaled up or down based on the viewport width, multiple images can be designed to more nicely fill the browser viewport.



The <picture> element contains two tags: one or more <source> tags and one <img> tag.

The browser will look for the first <source> element where the media query matches the current viewport width, and then it will display the proper image (specified in the srcset attribute). The <img> element is required as the last child of the <picture> element, as a fallback option if none of the source tags matches.



Tip: The <picture> element works "similar" to <video> and <audio>. You set up different sources, and the first source that fits the preferences is the one being used.



<picture>

​	<source media="(min-width:650px)" srcset="img_pink_flowers.jpg">

​	<source media="(min-width:465px)" srcset="img_white_flower.jpg">

​	<img src="img_orange_flowers.jpg" alt="Flowers" style="width:auto;">

</picture>





The <pre> tag defines preformatted text.

Text in a <pre> element is displayed in a fixed-width font, and the text preserves both spaces and line breaks. The text will be displayed exactly as written in the HTML source code.

Also look at:





**<source>**



The <source> tag is used to specify multiple media resources for media elements, such as <video>, <audio>, and <picture>.



The <source> tag allows you to specify alternative video/audio/image files which the browser may choose from, based on browser support or viewport width. The browser will choose the first <source> it supports.



<audio controls>

​	<source src="horse.ogg" type="audio/ogg">

​	<source src="horse.mp3" type="audio/mpeg">

​	Your browser does not support the audio element.

</audio>





**<progress>**



The <progress> tag represents the completion progress of a task.



Always add the <label> tag for best accessibility practices!



Use the <progress> tag in conjunction with JavaScript to display the progress of a task.



<label for="file">Downloading progress:</label>

<progress id="file" value="32" max="100"> 32% </progress>





**<ruby>**



The <ruby> tag specifies a ruby annotation. A ruby annotation is a small extra text, attached to the main text to indicate the pronunciation or meaning of the corresponding characters. This kind of annotation is often used in Japanese publications.



Use <ruby> together with <rt> and <rp>: The <ruby> element consists of one or more characters that needs an explanation/pronunciation, and an <rt> element that gives that information, and an optional <rp> element that defines what to show for browsers that do not support ruby annotations.



**<rp>**



The <rp> tag can be used to provide parentheses around a ruby text, to be shown by browsers that do not support ruby annotations.



Use <rp> together with <ruby> and <rt>: The <ruby> element consists of one or more characters that needs an explanation/pronunciation, and an <rt> element that gives that information, and an optional <rp> element that defines what to show for browsers that not support ruby annotations.



<ruby>

​	漢 <rp>(</rp><rt>ㄏㄢˋ</rt><rp>)</rp>

</ruby>



The <rt> tag defines an explanation or pronunciation of characters (for East Asian typography) in a ruby annotation.

Use <rt> together with <ruby> and <rp>: The <ruby> element consists of one or more characters that needs an explanation/pronunciation, and an <rt> element that gives that information, and an optional <rp> element that defines what to show for browsers that not support ruby annotations.





**<s>**



The <s> tag specifies text that is no longer correct, accurate or relevant. The text will be displayed with a line through it.

The <s> tag should not be used to define deleted text in a document, use the <del> tag for that.



<p><s>Only 50 tickets left!</s></p>

<p>SOLD OUT!</p>





<details>



The <details> tag specifies additional details that the user can open and close on demand.

The <summary> tag is used in conjunction with <details> to specify a visible heading for the details.



The <details> tag is often used to create an interactive widget that the user can open and close. By default, the widget is closed. When open, it expands, and displays the content within.

Any sort of content can be put inside the <details> tag. 



**<summary>**



The <summary> tag defines a visible heading for the <details> element. The heading can be clicked to view/hide the details.

The <summary> element should be the first child element of the <details> element.



<details>

​	<summary>Epcot Center</summary>

	<p>Epcot is a theme park at Walt Disney World Resort featuring exciting attractions, international pavilions, award-winning fireworks and seasonal special events.</p>

</details>





**<noscript>**



The <noscript> tag defines an alternate content to be displayed to users that have disabled scripts in their browser or have a browser that doesn't support script.

The <noscript> element can be used in both <head> and <body>. When used inside <head>, the <noscript> element could only contain <link>, <style>, and <meta> elements.





**<template>**



The <template> tag is used as a container to hold some HTML content hidden from the user when the page loads.

The content inside <template> can be rendered later with a JavaScript.

You can use the <template> tag if you have some HTML code you want to use over and over again, but not until you ask for it. To do this without the <template> tag, you have to create the HTML code with JavaScript to prevent the browser from rendering the code.



<button onclick="showContent()">Show hidden content</button>



<template>

 <h2>Flower</h2>

  <img src="img_white_flower.jpg" width="214" height="204">

</template>



<script>

function showContent() {

 let temp = document.getElementsByTagName("template")[0];

 let clon = temp.content.cloneNode(true);

 document.body.appendChild(clon);

}

</script>



**<time>**



The <time> tag defines a specific time (or datetime).

The datetime attribute of this element is used translate the time into a machine-readable format so that browsers can offer to add date reminders through the user's calendar, and search engines can produce smarter search results.



<p>Open from <time>10:00</time> to <time>21:00</time> every weekday.</p>



<p>I have a date on <time datetime="2008-02-14 20:00">Valentines day</time>.</p>





**<track>**



The <track> tag specifies text tracks for <audio> or <video> elements.



This element is used to specify subtitles, caption files or other files containing text, that should be visible when the media is playing.

Tracks are formatted in WebVTT format (.vtt files).



A video with subtitle tracks for two languages:

<video width="320" height="240" controls>

​	<source src="forrest_gump.mp4" type="video/mp4">

​	<source src="forrest_gump.ogg" type="video/ogg">

​	<track src="fgsubtitles_en.vtt" kind="subtitles" srclang="en" label="English">

​	<track src="fgsubtitles_no.vtt" kind="subtitles" srclang="no" label="Norwegian">

</video>**CSS3**







**outline**



An outline is a line that is drawn around elements, OUTSIDE the borders, to make the element "stand out".



Outline differs from borders! Unlike border, the outline is drawn outside the element's border, and may overlap other content. Also, the outline is NOT a part of the element's dimensions; the element's total width and height is not affected by the width of the outline.



CSS has the following outline properties:

outline-style

outline-color

outline-width

outline-offset

outline



The outline-width property specifies the width of the outline, and can have one of the following values:

thin (typically 1px)

medium (typically 3px)

thick (typically 5px)

A specific size (in px, pt, cm, em, etc)
