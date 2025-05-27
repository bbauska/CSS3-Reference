---
title: |
  CSS3 Reference Guide
  by Brian Bauska
author: "bbauska"
date last editted: "5/21/2025 Wed 2+pm"
date last editted: "5/22/2025 Thu 1+pm"
output: 
  markdown:
    with some style
---

<!--
ul.no-bullets {
  list-style-type: none; /* Remove bullets */
  padding: 0; /* Remove padding */
  margin: 0; /* Remove margins */
}
-->
<h1 align="center">CSS Reference Guide</h1>
<h6 align="center">(by Brian Bauska)</h6>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--~~~~~~~~~~~~~~~~~ readme.md of css3-ref.bauska.org ~~~~~~~~~~~~~~~~~-->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ 01. css reference guide logo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p align="center">
<img class="displayed"
  src="/images/image000.png?raw=true"
  title="CSS3 Reference Guide"
  alt="CSS3 Reference Guide."
  style="width:20%;" />
</p>

## CSS3 Reference Guide

### [Table of Contents](#table-of-contents)

## Preface

## Chapter 1: Basic Concepts
>### 1.1 [**Adding Styles to HTML**](#ch1-1-1)
>### 1.2 [**Rule Structure**](#ch1-2-1)
>### 1.3 [**At-rules**](#ch1-3-1)
>### 1.4 [**Comments**](#ch1-4-1)
>### 1.5 [**Style Precedence**](#ch1-5-1)
>### 1.6 [**Element Classification**](#ch1-6-1)
>### 1.7 [**Element Display Roles**](#ch1-7-1)
>### 1.8 [**Basic Visual Layout**](#ch1-8-1)
>### 1.9 [**Floating**](#ch1-9-1)
>### 1.10 [**Positioning**](#ch1-10-1)
>### 1.11 [**Flexible Box Layout**](#ch1-11-1)
>### 1.12 [**Grid Layout**](#ch1-12-1)
>### 1.13 [**Table Layout**](#ch1-13-1)

## Chapter 2: Values
>### 2.1 [**Keywords**](#ch2-1-1)
>### 2.2 [**Color Values**](#ch2-2-1)
>### 2.3 [**Number Values**](#ch2-3-1)
>### 2.4 [**Percentage Values**](#ch2-4-1)
>### 2.5 [**Length Values**](#ch2-5-1)
>### 2.6 [**Fraction Values**](#ch2-6-1)
>### 2.7 [**URIs**](#ch2-7-1)
>### 2.8 [**Angles**](#ch2-8-1)
>### 2.9 [**Times**](#ch2-9-1)
>### 2.10 [**Frequencies**](#ch2-10-1)
>### 2.11 [**Position**](#ch2-11-1)
>### 2.12 [**Strings**](#ch2-12-1)
>### 2.13 [**Identifiers**](#ch2-13-1)
>### 2.14 [**Attribute Values**](#ch2-14-1)
>### 2.15 [**Calculation Values**](#ch2-15-1)
>### 2.16 [**Variable Values**](#ch2-16-1)

## Chapter 3: Selectors and Queries
>### 3.1 [**Selectors**](#ch3-1-1)
>### 3.2 [**Structural Pseudo-Classes**](#ch3-2-1)
>### 3.3 [**The Negation Pseudo-Classes**](#ch3-3-1)
>### 3.4 [**Interaction Pseudo-Classes**](#ch3-4-1)
>### 3.5 [**Pseudo-Elements**](#ch3-5-1)
>### 3.6 [**Media Queries**](#ch3-6-1)
>### 3.7 [**Feature Queries**](#ch3-7-1)

## Chapter 4: Property Reference
>### 4.1 [**Inheritance and Animation**](#ch4-1-1)
>### 4.2 [**Value Syntax Conventions**](#ch4-2-1)
>### 4.3 [**Universal Values**](#ch4-3-1)
>### 4.4 [**Properties**](#ch4-4-1)

<!-- page v -->
<h2 style="text-align:right;">Preface</h2>
<p>Cascading Style Sheets (CSS) is the World Wide Web Consortium (W3C)
standard for the visual presentation of web pages (although it can be
used in other settings as well). After a short introduction to the key
concepts of CSS, this pocket reference provides an alphabetical
reference to all CSS3 selectors, followed by an alphabetical reference
to CSS3 properties.</p>

<!-- page 1 -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h2 id="ch1">1. CHAPTER 1 Basic Concepts</h2>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch1-1-1">1.1. Adding Styles to HTML</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>Styles can be applied to documents in three distinct ways, as discussed in the 
following sections.</p>

<h4>Inline Styles</h4>
In HTML, style information can be specified for an individual element
via the style attribute. The value of a style attribute is a
<i>declaration block</i> (see the section "Rule Structure" on page 5) without
the curly braces:
<pre>
&lt;p style=&quot;color: red; background: yellow;&quot;&gt;Look out!
This text is alarmingly presented!&lt;/p&gt;
</pre>
Note that as of this writing, only the content of a single declaration
block can be used as a style attribute value. For example, it is not
possible to place hover styles (using :hover) in a style attribute, nor
can &#64;import be used in this context.

Although typical XML document languages (such as SVG) support the style
attribute, it is unlikely that <i>all</i> XML languages will support a
similar capability. Because of this---and especially because it
encourages poor authoring practices---authors are discouraged from using
the style attribute, and thus inline styles.

<!-- page 2 -->
<h4>Embedded Stylesheets</h4>
<p>A stylesheet can be embedded within an HTML document using the style
element:</p>
<pre>
<b>&lt;html&gt;&lt;head&gt;&lt;title&gt;</b>Stylin&apos;!<b>&lt;/title&gt;</b>
<b>&lt;style</b> type=&quot;text/css&quot;<b>&gt;</b>
<b>h1</b> {<b>color</b>: purple;}
<b>p</b> {<b>font-size</b>: smaller; <b>color</b>: gray;}
<b>&lt;/style&gt;</b>
<b>&lt;/head&gt;</b> &hellip;
<b>&lt;/html&gt;</b>
</pre>
<p>XML-based languages may or may not provide an equivalent capability;
always check the document type definition (DTD) to be certain.
While style elements are often found inside the head element, as shown
in the preceding example, this is not required. Sometimes stylesheets
are embedded near the end of a document for performance reasons.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h4>External Stylesheets</h4>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>Styles can be stored in a separate file. The primary advantage to using
a separate file is that when commonly used styles are collected in a
single file, all pages using those styles can be updated by editing a
single stylesheet. A downside is that it's generally more efficient to
embed all styles (and scripts) into an HTML document in order to reduce
network calls, although this downside will disappear as HTTP/2 usage
increases.<p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h4>An external stylesheet can be referenced in one of three ways.</h4>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h5>1. <b>&#64;import directive</b></h5>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>One or more &#64;import directives can be placed at the beginning of any
stylesheet. For HTML documents, this is done within an embedded
stylesheet:</p>
<!-- page 3 -->

<pre>
<b>&lt;head&gt;&lt;title&gt;</b>My Document<b>&lt;/title&gt;</b>
<b>&lt;style</b> type=&quot;text/css&quot;<b>&gt;</b>
<b>&#64;import</b> url(site.css);
<b>&#64;import</b> url(navbar.css);
<b>&#64;import</b> url(footer.css) <b>screen</b> <b>and</b> (<b>min-width</b>: 960px);
<b>body</b> {<b>background</b>: yellow;}
<b>&lt;/style&gt;</b>
<b>&lt;/head&gt;</b>
</pre>
<p>Note that &#64;import directives can appear at the top (and, according to
the specification, <i>only</i> at the top) of any stylesheet. Thus, one
stylesheet could import another, which in turn would import a third.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h5>2. link element</h5>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>In HTML documents, the link element can be used to associate a
stylesheet with a document. Multiple link elements are permitted. The
media attribute can be used to restrict a stylesheet to one or more
media environments:</p>
<pre>
<b>&lt;head&gt;</b>
<b>&lt;title&gt;</b>A Document<b>&lt;/title&gt;</b>
<b>&lt;link</b> rel=&quot;stylesheet&quot; type=&quot;text/css&quot; href=&quot;basic.css&quot;
  media=&quot;all&quot;<b>&gt;</b>
<b>&lt;link</b> rel=&quot;stylesheet&quot; type=&quot;text/css&quot; href=&quot;web.css&quot;
  media=&quot;screen and (max-width: 960px)&quot;<b>&gt;</b>
<b>&lt;link</b> rel=&quot;stylesheet&quot; type=&quot;text/css&quot; href=&quot;paper.css&quot;
  media=&quot;print and (color-depth: 2)&quot;<b>&gt; &lt;/head&gt;</b>
</pre>
<p>It is also possible to link to alternate stylesheets, but few browsers
provide a way for users to make use of them. As of this writing, most or
all known user agents load all linked stylesheets, including the
alternate stylesheets, regardless of whether the user ever needs them.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h5>xml-stylesheet processing instruction</h5>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>In XML documents (such as XHTML documents sent with a MIME type of
text/xml, application/xml, or application/ xhtml+xml), an xml-stylesheet
processing instruction can be used to associate a stylesheet with a
document. Any xmlstylesheet processing instructions must be placed in
the prolog of an XML document. Multiple xml-stylesheet processing
instructions are permitted. The media pseudo-attribute can be used to
restrict a stylesheet to one or more forms of media:</p>
<!-- page 4 -->
<pre>
&lt;?xml-stylesheet type=&quot;text/css&quot; href=&quot;basic.css&quot;
  media=&quot;all&quot;?&gt;
&lt;?xml-stylesheet type=&quot;text/css&quot; href=&quot;web.css&quot;
  media=&quot;screen&quot;?&gt;
&lt;?xml-stylesheet type=&quot;text/css&quot; href=&quot;paper.css&quot;
  media=&quot;print&quot;?&gt;
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h5>3. <b>HTTP Link headers</b></h5>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>The last (and least common by far) way of associating an external
stylesheet with your pages is to use an HTTP Link header. This approach
uses HTTP headers to replicate the effects of a link element or &#64;import
directive.</p>
<p>Adding a line such as this to the <i>.htaccess</i> file at the root level of
your server will make this happen for all pages on the site, where
/style.css is the server path of the stylesheet to be loaded:</p>
<pre>
  &quot;&lt;/style.css&gt;;rel=stylesheet;type=text/css;media=all&quot;
</pre>
<h5>Explanation of the attributes:</h5>
<pre>rel="stylesheet":</pre>
<p>This attribute indicates that the linked file is a stylesheet, which defines how 
the HTML content should be displayed.</p>
<pre>href="style.css":</pre>
<p>This attribute specifies the URL of the CSS file to be linked.</p>
<pre>type="text/css":</pre>
<p>This attribute specifies the MIME type of the linked file, indicating that it is 
a CSS file. While technically redundant, it's good practice to include it for clarity.</p>
<pre>media="all":</pre>
<p>This attribute specifies that the stylesheet applies to all media types. This 
means it will be applied to screens, printers, and any other media for which the 
browser supports style sheets. If you want to target specific devices, you can use 
other media types like screen, print, or speech or use media queries.</p>
<p>As an alternative to using <i>.htaccess</i>, which has been known to cause
performance problems, you can edit your <i>httpd.conf</i> file to do the same
thing:</p>
<pre>
&lt;Directory /usr/local/username/httpdocs&gt;
  &quot;&lt;/style.css&gt;;rel=stylesheet;type=text/css;media=all&quot;
&lt;/Directory&gt; 
</pre>
<p>where /usr/local/username/httpdocs is replaced with the
Unix pathname of your website's actual home directory, and /style.css is
replaced with the location of the stylesheet within that home directory.</p>
<p>As of this writing, HTTP headers were not supported by all user agents,
most notably Internet Explorer and Safari. Thus, this technique is
usually limited to production environments based on other user agents,
and the occasional Easter egg for Firefox and Opera users.</p>
<!-- page 5 -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch1-2-1">Rule Structure</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>A stylesheet consists of one or more <i>rules</i> that describe how page
elements should be presented. Every rule has two fundamental parts: the
<i>selector</i> and the <i>declaration block</i>. Figure 1-1 illustrates the
structure of a rule.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ 01. rule structure ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p align="center">
<img class="displayed"
  src="/images/image001.png?raw=true"
  title="Rule structure"
  alt="Rule structure."
  style="width:50%;" />
</p>
<!-- image001 rule structure -->
<p align="center"><i>Figure 1-1. Rule structure</i></p>
<p>On the left side of the rule, we find the selector, which selects the
parts of the document to which the rule should be applied. Selectors can
stand singly or be grouped as a comma-separated list; e.g., to select
the top three heading levels at once, the selector group would be h1,
h2, h3. On the right side of the rule, we have the declaration block. A
declaration block is made up of one or more <i>declarations</i>; each
declaration is a combination of a CSS <i>property</i> and a <i>value</i> of that
property.</p>
<p>The declaration block is always enclosed in curly braces. A declaration
block can contain several declarations; each declaration must be
terminated with a semicolon (;). The exception is the final declaration
in a declaration block, for which the semicolon is optional (though
recommended).</p>
<p>Each property, which represents a particular stylistic parameter, is
separated from its value by a colon (:). Property names in CSS are not
case-sensitive. Legal values for a property are defined by the property
description. Chapter 4 provides details on acceptable values for CSS
properties.</p>
<!-- page 6 -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch1-3-1">1.3. <b><mark>&#64; At-rules</mark></b></h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>A CSS <i>at-rule</i> is a statement or block of rules that begins with a specific 
identifier preceded by an @ sign. These are:</p>
<ul>
  <li><b><mark>&#64;charset</mark></b><br>
    Allows an author to define the encoding of the styles within the
	stylesheet (e.g., &#64;charset &quot;utf-8&quot;;). This enables authors to
	define the encoding of their styles even when they do not control the
	encoding of the file or system in which the styles are written. If
	multiple &#64;charset rules are declared, only the first will be used.
	This <i>must</i> be the first line of a stylesheet in which it appears, and
	<i>cannot</i> be preceded by any character. &#64;charset cannot be used in a
	stylesheet embedded in a document.</li>
  <li><b><mark>&#64;import</mark></b><br>
    Allows an author to include the styles of another stylesheet (see
	"@import directive" on page 2). Multiple &#64;import rules are permitted. 
	Any &#64;import rules <i>must</i> appear before all other parts of the stylesheet 
	except for &#64;charset.</li>
  <li><b><mark>&#64;namespace</mark></b><br>
    Allows an author to define an XML namespace to be used in selectors
	(e.g., &#64;namespace svg url(http:// www.w3.org/2000/svg);, permitting
	the use of svg&vert;a {color: black;} to select &lt;a&gt; elements within SVG
	files differently than &lt;a&gt; elements in HTML). Multiple &#64;namespace 
	rules are permitted. Any &#64;namespace <i>must</i> appear before all other parts 
	of the stylesheet except for &#64;charset and &#64;import rules.</li>
</ul>
<p>Besides these statements, there are a number of conditional at-rules.
These include:</p>

<ul>
  <li><b><mark>&#64;counter-style</mark></b><br>
    Defines symbol and counting patterns used in CSS counters (e.g., the
	numbering of list items in an ordered list).</li>
  <li><b><mark>&#64;font-face</mark></b><br>
    Defines an external font to be downloaded and used, including
	definitions of the identifiers to be used in other style rules. This
	is part of what is often called "web fonts" or "custom fonts."</li>
  <li><b><mark>&#64;keyframes</mark></b><br>
    Defines the states of various steps in an animation sequence, grouped
	together under a unique identifier.</li>
  <li><b><mark>&#64;media</mark></b><br>
    Defines the media types and parameters in which a block of styles are
	to be applied: e.g., writing &#64;media (maxwidth: 600px) and then the
	styles to be used for smaller screens. This is the key to Responsive
	Web Design.</li>
  <li><b><mark>&#64;supports</mark></b><br>
    Defines the browser-support conditions under which a block of styles
	should be used: e.g., writing &#64;supports (display: grid) and then 
	the styles that should be used in a CSS Grid--supporting browser.</li>
</ul>
<p>There are other proposed at-rules which are, as of early 2018, at various stages of 
development. These include &#64;document, &#64;font-feature-values, &#64;page, and 
&#64;viewport.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch1-4-1">1.4. Comments</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>Including comments in CSS is simple. You open with /&ast; and end with &ast;/,
like this:</p>
<pre>/&ast; This is a comment! &ast;/</pre>
<p>Comments can be multiple lines long:</p>
<pre>/&ast; This is a comment!
This is a continuation of the comment.
And so is this. &ast;/</pre>
<p>They can also occur anywhere within a stylesheet except in the middle of
a property name or value:</p>

<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h4>Comments</h4>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<pre>
<b>h1</b>/&ast; heading-level-1 &ast;/ {color /&ast; foreground color &ast;/:
  rgba(23,58,89,0.42) /&ast; RGB + opacity &ast;/;}
</pre>

<p>HTML (properly SGML) comments &lt;!&dash;- such as this &dash;-&gt; are permitted in
stylesheets so as to hide the styles from browsers so old that they don't understand HTML 
3.2. They do <i>not</i> act as CSS comments; that is, anything contained in an HTML comment 
will be seen and interpreted by the CSS parser.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch1-5-1">1.5. Style Precedence</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>A single HTML document can import and link to multiple external stylesheets, contain 
one or more embedded stylesheets, and make use of inline styles. In the process, it is 
quite possible that some rules will conflict with one another. Cascading Style Sheets 
uses a mechanism called the <i>cascade</i> to resolve any such conflicts and arrive at a 
final set of styles to be applied to the document. Two key components of the cascade are 
specificity and inheritance.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h4>Specificity Calculations</h4>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p><i>Specificity</i> describes the weight of a selector and any declarations associated 
with it. Table 1-1 shows how much each part of a selector contributes to the total 
specificity of that selector.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ 02. selector type specificity ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p align="center">
<img class="displayed"
  src="/images/image002.png?raw=true"
  title="Selector type specificity"
  alt="Selector type specificity."
  style="width:40%;" />
</p>

<!-- image002 -->
<p align="center"><i>Table 1-1. Selector type specificity</i></p>

<p>Specificity values are cumulative; thus, a selector containing two element identifiers 
and a class identifier (e.g., div.aside p) has a specificity of 0,0,1,2. Specificity values 
are sorted from right to left; thus, a selector containing 11 element identifiers (0,0,0,11) 
has a lower specificity than a selector containing just a single class identifier (0,0,1,0).</p>
<p>The !important directive gives a declaration more weight than nonimportant declarations. 
The declaration retains the specificity of its selectors and is used only in comparison 
with other important declarations.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h4>Inheritance</h4>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>The elements in a document form a treelike hierarchy, with the root element at the top 
and the rest of the document structure spreading out below it (which makes it look more 
like a tree root system, really). In an HTML document, the html element is at the top of 
the tree, with the head and body elements descending from it. The rest of the document
structure descends from those elements. In such a structure, elements lower down in the 
tree are descendants of the ancestors, which are higher in the tree.</p>

<p>CSS uses the document tree for the mechanism of <i>inheritance</i>, in which a style 
applied to an element is inherited by its descendants. For example, if the body element 
is set to have a color of red, that value propagates down the document tree to the elements 
that descend from the body element. Inheritance is interrupted only by a conflicting style
rule that applies directly to an element. Inherited values have no specificity at all 
(which is <i>not</i> the same as having zero specificity).</p>

<p>Note that some properties are not inherited. A property will always define whether it 
is inherited. Some examples of noninherited properties are padding, border, margin, and 
background.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h4>The Cascade</h4>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>The cascade is how CSS resolves conflicts between styles; in other words, it is the 
mechanism by which a user agent decides, for example, what color to make an element when 
two different rules apply to it and each one tries to set a different color.<br>
Here's how the cascade works:</p>
<ol>
  <li>Find all rules with a selector that matches a given element.</li>
  <li>Sort all declarations applying to the given element by <i>explicit weight</i>. 
    Those rules that are marked !important have a higher explicit weight than those 
	that are not.</li>
  <li>Sort all declarations applying to the given element by <i>origin</i>. There are 
    three basic origins: author, reader, and user agent. Under normal circumstances, 
	the author's styles win out over the reader's styles. Howerver, !important reader 
	styles are stronger than any other styles, including !important author styles. 
	Both author and reader styles override the user agent's default styles.</li>
  <li>Sort all declarations applying to the given element by <i>specificity</i>. Those 
    elements with a higher specificity have more weight than those with lower specificity.</li>
  <li>Sort all declarations applying to the given element by <i>order</i>. The later a 
    declaration appears in the stylesheet or document, the more weight it is given. 
	Declarations that appear in an imported stylesheet are considered to come before 
	all declarations within the stylesheet that imports them.</li>
</ol>
<p>Any presentational hints that come from non-CSS sources (e.g., the preference dialog 
within a browser) are given the same weight as the user agent's default styles (see 
step 2 above).</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch1-6-1">1.6 Element Classification</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>Broadly speaking, CSS groups elements into two types: <i>nonreplaced</i> and <i>replaced</i>. 
Although the types may seem rather abstract, there actually are some profound differences in how 
the two types of elements are presented. These differences are explored in detail in Chapter 7 of 
<a href="http://shop.oreilly.com/product/0636920012726.do"><i>CSS: The</i> <i>Definitive Guide</i>, 
4th Edition</a> (O'Reilly).</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h4>Nonreplaced Elements</h4>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>The majority of HTML elements are <i>nonreplaced elements</i>, which means their content is 
presented by the user agent inside a box generated by the element itself. For example, 
&lt;span&gt;hi there&lt;/span&gt; is a nonreplaced element, and the text hi there will be 
displayed by the user agent. Paragraphs, headings, table cells, lists, and almost everything
else in HTML are nonreplaced elements.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h4>Replaced Elements</h4>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>In contrast, <i>replaced elements</i> are those whose content is replaced by something 
not directly represented by document content. The most familiar HTML example is the img 
element, which is replaced by an image file external to the document itself. In fact, 
img itself has no actual content, as we can see by considering a simple example:</p>
<pre>
  <b>&lt;img</b> src=&quot;howdy.gif&quot; alt=&quot;Hi&quot;<b>&gt;</b>
</pre>
<p>There is no content contained in the element---only an element name and attributes. 
Only by replacing the element's lack of content with content found through other means 
(in this case, loading an external image specified by the src attribute) can the element 
have any presentation at all. Another example is the input element, which may be replaced 
with a radio button, checkbox, or text input box, depending on its type. Replaced 
elements also generate boxes in their display.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch1-7-1">1.7. Element Display Roles</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>In addition to being replaced or not, there are two basic types of element display roles 
in CSS: <i>block-level</i> and <i>inline-level</i>. All CSS display values fall into one 
of these two categories. It can be important to know which general role a box falls into, 
since some properties only apply to one type or the other.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h4>Block-Level</h4>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p><i>Block-level boxes</i> are those where the element box (by default) fills its 
parent element's content area width and cannot have other elements to its sides. In 
other words, block-level elements generate "breaks" before and after the element box. 
The most familiar block elements from HTML are p and div. Replaced elements can be 
block-level elements but usually are not.</p>
<p>List items are a special case of block-level elements. In addition to behaving in 
a manner consistent with other block elements, they generate a marker---typically a 
bullet for unordered lists or a number for ordered lists---which is "attached" to 
the element box. Except for the presence of this marker, list items are identical 
to other block elements.</p>

<p>As of early 2018, the display values that create block boxes are block, list-item, 
table, table-row-group, table-headergroup, table-footer-group, table-column-group, 
table-row, table-column, table-cell, table-caption, flex, and grid.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h4>Inline-Level</h4>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p><i>Inline-level</i> boxes are those where an element box is generated within
a line of text and does not break up the flow of that line. Perhaps the
best-known inline element is the a element in HTML. Other examples are
span and em. These elements do not generate a break before or after
themselves, so they can appear within the content of another element
without disrupting its display.</p>

<p>Note that although the CSS block and inline elements have a great deal
in common with HTML block- and inline-level elements, there is an
important difference. In HTML, block-level elements cannot descend from
inline-level elements, whereas in CSS, there is no restriction on how
display roles can be nested within each other.</p>

<p>The display values that create inline boxes are: inline, inlineblock,
inline-table, and ruby. As of this writing, it was not explicitly
defined that the various Ruby-related values (e.g., ruby-text) also
generate inline boxes, but this seems the most likely outcome.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch1-8-1">1.8. Basic Visual Layout</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>CSS defines algorithms for laying out any element in a document. These
algorithms form the underpinnings of visual presentation in CSS. There
are two primary kinds of layout, each with very different behaviors:
<i>block-level</i> and <i>inline-level</i> layout.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h4>Block-Level Layout</h4>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>A block-level box in CSS generates a rectangular box called the <i>element
box</i>, which describes the amount of space occupied by an element. Figure
1-2 shows the components of an element box.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ 03. the complete box model ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p align="center">
<img class="displayed"
  src="/images/image003.png?raw=true"
  title="The complete box model"
  alt="The complete box model."
  style="width:60%;" />
</p>
<!-- image003 -->
<p align="center"><i>Figure 1-2. The complete box model</i></p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h4>The following rules apply to an element box:</h4>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<ul>
  <li>By default, the background of the element box extends to the outer edge of the 
    border, thus filling the content, padding, and border areas (though this can be 
	changed with background-clip). If the border has any transparent portions (e.g., it 
	is dotted or dashed), the element background will be visible in those portions. The
    background does not extend into the margin areas of the box. Any outlines are drawn 
	in the margin area and do not affect layout.</li>
  <li>Only the margins, height, and width of an element box may be set to auto.</li>
  <li>Only margins can be given negative values.</li>
  <li>The padding and border widths of the element box default to 0 (zero), and the 
    border style defaults to none.</li>
  <li>If box-sizing is content-box (the default value), the property width
    defines only the width of the content area; any padding, borders, or
    margins are added to it. The same is true for height with respect to
    the height.</li>
  <li>If box-sizing is padding-box, the property width defines the total
    width of the content and the padding. Any borders and margins are
    added to it. The same is true for height with respect to the height.</li>
  <li>If box-sizing is border-box, the property width defines the total
    width of the content, padding, and borders; any margins are added to
    it. The same is true for height with respect to the height.</li>
</ul>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h4>Inline Layout</h4>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>An inline-level box in CSS generates one or more rectangular boxes
called <i>inline boxes</i>. The following rules apply to inline boxes:</p>
<ul>
  <li>width and height do not apply to nonreplaced inline boxes.</li>
  <li>For the properties left, right, top, bottom, margin-left, margin-right, 
    margin-top, and margin-bottom, any value of auto is converted to 0 (zero).</li>
  <li>For replaced inline boxes, the following rules apply:
    <ul>
	  <li>If height and width are both auto and the element has an intrinsic
	  width (e.g., an image), the value of width is equal to the element's
	  intrinsic width. The same holds true for height.</li>
	  <li>If height and width are both auto and the element does not have an
	  intrinsic width but does have an intrinsic height and layout ratio,
	  then width is set to be the intrinsic height times the ratio.</li>
	  <li>If height and width are both auto and the element does not have an
	  intrinsic height but does have an intrinsic width and layout ratio,
	  then height is set to be the intrinsic width divided by the ratio.</li>
	</ul>
  </li>
</ul>
<p>There are a few rules even more obscure than those last two; see 
<a href="http://w3.org/TR/css3-box/#inline-replaced">the CSS box model documentation</a>
for details.</p>

<p>All inline elements have a line-height, which has a great deal to do
with how the elements are displayed. The height of a line of text is
determined by taking the following factors into account:</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h5><i>Anonymous text</i></h5>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<ul>
  <li>Any string of characters not contained within an inline element. Thus, in the markup:<br>
    <b>&lt;p&gt;</b>I&apos;m <b>&lt;em&gt;</b>so<b>&lt;/em&gt;</b> happy!<b>&lt;/p&gt;</b><br>
    the sequences "I'm " and " happy!" are anonymous text. Note that the spaces are part 
    of the anonymous text, as a space is a character like any other.</li>
</ul>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h5><i>Em-box</i></h5>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<ul>
  <li>The space taken up by a capital letter M in the given font; otherwise known as 
    the character box. Actual glyphs can be taller or shorter than their em-boxes, as 
	discussed in Chapter 5 of <a href="http://shop.oreilly.com/product/0636920012726.do">
	<i>CSS: The Definitive Guide</i></a>, the value of font-size determines the height 
	of each em-box.</li>
</ul>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h5><i>Content area</i></h5>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<ul>
  <li>In nonreplaced elements, this can be the box described by the em-boxes of every 
    character in the element, strung together, or else the box described by the character 
	glyphs in the element. In CSS2.1 and later, user agents can choose either. This text 
	uses the em-box definition for simplicity's sake. In replaced elements, the content 
	area is the intrinsic height of the element plus any margins, borders, or padding.</li>
</ul>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h5><i>Leading</i></h5>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<ul>
  <li>The difference between the values of font-size and lineheight. Half this difference 
    is applied to the top and half to the bottom of the content area. These additions to 
	the content area are called, not surprisingly, <i>half-leading</i>. Leading is 
	applied only to nonreplaced elements.</li>
</ul>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h5><i>Inline box</i></h5>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<ul>
  <li>The box described by the addition of the leading to the content area. For nonreplaced 
    elements, the height of the inline box of an element will be equal to the value for 
	line-height. For replaced elements, the height of the inline box of an element will be 
	equal to the content area, as leading is not applied to replaced elements.</li>
</ul>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h5><i>Line box</i></h5>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<ul>
  <li>The shortest box that bounds the highest and lowest points of the inline boxes that 
    are found in the line. In other words, the top edge of the line box will be placed 
	along the top of the highest inline box top, and the bottom of the line box is placed 
	along the bottom of the lowest inline box bottom. (See Figure 1-3).</li>
</ul>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ 04. inline layout details ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p align="center">
<img class="displayed"
  src="/images/image004.png?raw=true"
  title="Inline layout details"
  alt="Inline layout details."
  style="width:50%;" />
</p>
<!-- image004 -->
<p align="center"><i>Figure 1-3. Inline layout details</i></p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch1-9-1">1.9. Floating</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>Floating allows an element to be placed to the left or right of its
containing block (which is the nearest block-level ancestor element),
with following content flowing around the element. Any floated element
automatically generates a block box, regardless of what type of box it
would generate if not floated. A floated element is placed according to
the following rules:</p>
<ul>
  <li>The left (or right) outer edge of a floated element may not be to the left (or right) 
    of the inner edge of its containing block.</li>
  <li>The left (or right) outer edge of a floated element must be to the right (or left) 
    of the right (left) outer edge of a leftfloating (or right-floating) element that 
	occurs earlier in the document's source, unless the top of the latter element is 
	below the bottom of the former.</li>
  <li>The right outer edge of a left-floating element may not be to the right of the left 
    outer edge of any right-floating element to its right. The left outer edge of a 
	right-floating element may not be to the left of the right outer edge of any 
	left-floating element to its left.</li>
  <li>A floating element's top may not be higher than the inner top of its containing block.</li>
  <li>A floating element's top may not be higher than the top of any earlier floating or 
    block-level element.</li>
  <li>A floating element's top may not be higher than the top of any line box with content 
    that precedes the floating element.</li>
  <li>A left (or right) floating element that has another floating element to its left 
    (right) may not have its right (left) outer edge to the right (left) of its 
	containing block's right (left) edge.</li>
  <li>A floating element must be placed as high as possible.</li>
  <li>A left-floating element must be put as far to the left as possible, and a right-floating 
    element as far to the right as possible. A higher position is preferred to one that is 
	farther to the right or left.</li>
</ul>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch1-10-1">1.10. Positioning</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>When elements are positioned, a number of special rules come into play. These rules 
govern not only the containing block of the element, but also how it is laid out within 
that element.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h4>Types of Positioning</h4>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>There are five types of positioning:</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h5><i>Static</i></h5>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<ul>
  <li>The element's box is generated as normal. Block-level elements generate a rectangular 
    box that is part of the document's flow, and inline-level boxes generate one or more 
	line boxes that flow within their parent element.</li>
</ul>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h5><i>Relative</i></h5>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<ul>
  <li>The element's box is offset by some distance. Its containing block can be considered 
    to be the area that the element would occupy if it were not positioned. The element 
	retains the shape it would have had were it not positioned, and the space that the 
	element would otherwise have occupied in the normal flow is preserved.</li>
</ul>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h5><i>Absolute</i></h5>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<ul>
  <li>The element's box is completely removed from the flow of the document and positioned 
    with respect to its containing block, which may be another element in the document or 
	the initial containing block (described in the next section). Whatever space the element 
	might have occupied in the normal document flow is closed up, as though the element did 
	not exist. The positioned element generates a block box, regardless of the type of box 
	it would generate if it were in the normal flow.</li>
</ul>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h5><i>Sticky</i></h5>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<ul>
  <li>The element's box stays in the normal flow until it reaches a sticky edge of the 
    containing box, at which time it "sticks" there as if absolutely positioned. The space 
	that the element would otherwise have occupied in the normal flow is preserved.</li>
</ul>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h5><i>Fixed</i></h5>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<ul>
  <li>The element's box behaves as though set to absolute, but its containing block is 
    the viewport itself.</li>
</ul>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h4>The Containing Block</h4>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>The containing block of a positioned element is determined as follows:</p>
<ol type="1">
  <li>The containing block of the <i>root element</i> (also called the <i>initial
    containing block</i>) is established by the user agent. In HTML, the
    root element is the html element, although some browsers may use
    body.</li>
  <li>For nonroot elements, if an element's position value is relative or static, its 
    containing block is formed by the content edge of the nearest block-level, table-, 
	cell-, or inline-block ancestor box. Despite this rule, relatively positioned
	elements are still simply offset (not positioned with respect to the containing 
	block described here) and statically positioned elements do not move from their 
	place in the normal flow.</li>
  <li>For nonroot elements that have a position value of absolute, the containing block 
    is set to the nearest ancestor (of any kind) that has a position value other than 
	static, a filter value other than none, or a transform value other than none. This 
	happens as follows:
    <ol type="a">
	  <li>If the ancestor is block-level, the containing block is that element's outer 
	    padding edge; in other words, it is the area bounded by the element's border.</li>
      <li>If the ancestor is inline-level, the containing block is set to the content 
	    edge of the ancestor. In left-to-right languages, the top and left of the 
		containing block are the top and left content edges of the first box in the 
		ancestor, and the bottom and right edges are the bottom and right content edges 
		of the last box. In rightto-left languages, the right edge of the containing 
		block corresponds to the right content edge of the first box, and the left is 
		taken from the last box. The top and bottom are the same.</li>
      <li>If there are no ancestors as described in 3a and 3b, the absolutely positioned 
	    element's containing block is defined to be the initial containing block.</li>
    </ol>
  </li>
</ol>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch1-11-1">1.11. Flexible Box Layout</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>Flexible box layout (also known as <i>flexbox</i> or <i>flex layout</i>) is ideal for 
almost any one-dimensional layout; that is, situations where a number of elements need 
to be placed and distributed along a line. There are two kinds of flex elements: the 
<i>flex container</i> and the <i>flex items</i> that are placed within the container.</p>

<p>All the direct children of the flex container element are flex items.</p>

<p>There are two kinds of flex containers: block flexboxes (display: flex) and inline 
flexboxes (display: inline-flex). These are very much like block and inline-block boxes.</p>
<p>Flex items are laid out in a single line by default, even if this causes the flex items 
to overflow the flex container. This behavior can be changed using the flex-wrap property.</p>

<p>Figure 1-4 shows the values (and their effects) of the justify content and align-items 
properties.</p>
<!-- image00 -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ 05. justify and align values ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p align="center">
<img class="displayed"
  src="/images/image005.png?raw=true"
  title="Justify and align values"
  alt="Justify and align values."
  style="width:50%;" />
</p>
<p align="center"><i>Figure 1-4. Justify and align values</i></p>

<p>The process of calculating flex sizes is fairly complex. Here's a simplified version 
of the algorithm:</p>
<ol>
  <li>Add together all the hypothetical outer main sizes of the flex items in a flex 
    container. If the sum is smaller than the container size, the <i>flex factor</i> is 
	to grow; otherwise, the flex factor is to shrink.</li>
  <li>Any items that are inflexible are frozen in size. These are:
    <ul>
	  <li>Any item with a flex factor of zero</li>
	  <li>Any item whose <i>hypothetical main size</i> is greater (if growing) or
	    smaller (if shrinking) than its <i>base size</i></li>
 <li>Any item with a growth factor (if growing) or shrink factor (if shrinking) 
	  of zero.</li>
	</ul>
  <li>Calculate the <i>initial free space</i> by finding the difference between the outer 
    sizes of all flex items and the size of the flex container.</li>
  <li>Distribute the available free space to the flex items. The amount given to each flex 
    item is initially determined by the ratio of its flex factor to the sum of all the items' 
	flex factors. If an item will be grown past its maximum allowed size, or shrunk below its
    minimum allowed size, set the size to be the allowed maximum (if growing) or minimum (if 
	shrinking).</li>
</ol>

<p>Again, this is a simplified version of the actual flex sizing algorithm given in the 
<a href="https://www.w3.org/TR/css-flexbox-1/#resolve-flexible-lengths">
W3C documentation</a>. Consult section 9.7 of the CSS Flexible Box Layout Module Level 1 for
full details if you want to know more.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch1-12-1">1.12. Grid Layout</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>Grid layout is ideal for almost any two-dimensional layout. There are two kinds of 
grid elements: the <i>grid container</i> and the <i>grid items</i> that are placed within 
the container. All the direct children of the grid container element are grid items.</p>

<p>There are two kinds of grid containers: block grids (display: grid) and inline grids 
(display: inline-grid). These are very much like block and inline-block boxes.</p>

<p>A grid is made up of the following components, as illustrated in Figure 1-5:</p>
<ul>
  <li>A <i>grid line</i> is a horizontal or vertical dividing line within the
    grid container. These are placed as the author directs and create
    grid <i>cells</i>, <i>areas</i>, and <i>tracks</i> by implication. Grid lines can
    be labeled with <i>identifier tokens</i>; that's the basis of grid item
    placement.</li>
  <li>A <i>grid cell</i> is any space bounded by four grid lines, with no other
    grid lines running through it, analogous to a table cell. This is
    the smallest unit of area in grid layout. Grid cells cannot be
    directly addressed with CSS grid properties; that is, no property
    allows you to say a grid item should be associated with a given
    cell. (But see the next point for more details.)</li>
  <li>A <i>grid area</i> is any rectangular area bounded by four grid lines and
    made up of one or more grid cells. An area can be as small as a
    single cell or as large as all the cells in the grid. Grid areas are
    directly addressable by CSS grid properties, which allow you to
    define the areas and then associate grid items with them.</li>
  <li>A <i>grid track</i> is a continuous run between two adjacent grid
    lines---in other words, a <i>grid column</i> or a <i>grid row</i>. It goes
    from one edge of the grid container to the other. The size of a grid
    track is dependent on the placement of the grid lines that define
    it. Grid columns and rows are broadly analogous to table columns and
    rows. More generically, they can be referred to as <i>block axis</i> and
    <i>inline axis</i> tracks, where (in Western languages) column tracks are
    on the block axis and row tracks are on the inline axis.</li>
</ul>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ 06. Grid layout components ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p align="center">
<img class="displayed"
  src="/images/image006.png?raw=true"
  title="Grid layout components"
  alt="Grid layout components."
  style="width:50%;" />
</p>
<p align="center"><i>Figure 1-5. Grid layout components</i></p>

<p>The placement of grid lines can be quite complex, and is accomplished by
defining grid track sizes. Between each grid track, a grid line is
placed. These lines can be labeled with gridline names, or left
unlabeled and later addressed using numbers.</p>

<p>The formal syntax for defining grid track sizes is quite complicated,
but the components are relatively simple to list and explain:</p>

<h5><b><mark><i>&lt;length&gt; &vert; &lt;percentage&gt;</i></mark></b></h5>

<p>Any non-negative length or percentage value. Thus, 5em defines a 5-em
gap between grid lines, whereas 5% creates a gap between lines that is
5% of the total grid length in the given direction (i.e., the
horizontal length for grid rows, and the vertical length for columns).</p>

<h5><b><mark><i>&lt;flex&gt;</i></mark></b></h5>

<p>A positive real number with the unit identifier fr (e.g., 2fr or
3.14fr) which defines a <i>flex factor</i> for the grid track.</p>

<h5><b><mark>min-content</mark></b></h5>

<p>Sets the grid track's width (or height) to be as small as possible
while still containing all the content within the grid track. For
example, column tracks that contain only text will become as narrow as
the widest run of text that cannot be line-broken within the track.</p>

<h5><b><mark>max-content</mark></b></h5>

<p>Sets the grid track's width (or height) to be large enough to contain
the largest rendering of all the content within the grid track. For
example, column tracks that contain only text will become as wide as
the longest run of text, <i>without</i> any line-wrapping of the text.</p>

<h5><b><mark>auto</mark></b></h5>

<p>In most cases, auto is equivalent to the largest minimum size of the
grid items occupying the grid track; that is, once all the minimum
sizes of the grid items in the track have been determined, the track
is made as wide as the widest of those minimums. When auto is used as
a maximum value (see minmax() later in this list), it is identical to
max-content.</p>

<h5><b><mark>minmax(<i>&lt;min&gt;,&lt;max&gt;</i>)</mark></b></h5>
<p>Sets a range of sizes outside which the grid track cannot grow or shrink. Either <i>&lt;min&gt;</i> 
or <i>&lt;max&gt;</i> can be a <i>&lt;length&gt;</i> or <i>&lt;percentage&gt;</i> value, min-content, 
or max-content. <i>&lt;max&gt;</i> can be a <i>&lt;flex&gt;</i> value, but <i>&lt;min&gt;</i> cannot. 
If the minimum value computes to be larger than the maximum computed value, the maximum sizing is ignored 
and the minimum size is used as a minimum.</p>

<h5><b><mark>fit-content( &lbrack; <i>&lt;length&gt; &vert; &lt;percentage&gt;</i> &rbrack; )</mark></b></h5>
Equivalent to minmax(auto,max-content) with an exception: if the track's size is larger than the 
auto value's computed value, that size can't go higher than the given value (a <i>&lt;length&gt;</i> 
or <i>&lt;percentage&gt;</i>). This is intended to let authors declare a maximum track size while 
still letting the track size be content-bound below that maximum.

<h5><b><mark>repeat( &lbrack; <i>&lt;integer&gt; &vert;</i> auto-fill <i>&vert;</i> auto-fit &rbrack;, 
<i>&lt;track-list&gt;</i> )</mark></b></h5>
<p>Allows authors to repeat a pattern of grid track sizes as many times as they like. The 
<i>&lt;integer&gt;</i> value must be positive. auto-fill and auto-fit delegate the number of tracks 
to the user agent. <i>&lt;track-list&gt;</i> can be any valid combination of track sizes.</p>

<p>There are three kinds of track sizing. These are:</p>

<h5><b><i><mark>Fixed</mark></i></b></h5>

<p>Tracks are given a size in absolute lengths (such as px or em), or sized with %. 
Percentage values count as fixed track sizes because they are always the same for a 
given grid container size. The tracks' sizing does not depend on their contents.</p>

<h5><b><i><mark>Flexible</mark></i></b></h5>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Tracks are given a flex or fractional sizing via the fr 
unit. Their sizing does not depend on their contents.

<h5><b><i><mark>Intrinsic</mark></i></b></h5>
<p>The tracks' size is dependent on the things found within them; i.e., with min-content, 
max-content, fit-content(), and auto. These tracks may always be the same size for a given 
container size and set of content, but they are not regarded as fixed for layout purposes 
because their contents directly affect their sizing.</p>

<p>The process of actually determining the size of grid tracks, including
what to do when track sizes are overconstrained or could lead to
circular dependencies, is too long to go into here. In broad strokes,
this is the process to find the track sizes:</p>
<ol type="1"
  <li>Initialize track sizes, including determining the minimum and
    maximum sizes for each track. Resolve fixed track sizes to absolute
    length values. Set intrinsically sized tracks' minimum size to zero
    and maximum size to unlimited. Flexible tracks are left flexible,
    with an initial minimum size of zero.</li>
  <li>Determine the size of intrinsic (e.g., auto) tracks, resolving each
    to an absolute length. First find sizes based on the items within
    the track, and then gradually add space to encompass items that span
    multiple tracks.</li>
  <li>Maximize tracks up to their growth limit (this is determined
    automatically).</li>
  <li>Expand flexible (fr) tracks by adding space according to the ratio
    of each track's flex factor to the total of all flex factors in the
    grid track.</li>
  <li>Expand any auto-sized tracks by dividing the remaining free space
    (if any) by the number of auto tracks and expanding them equally.</li>
</ol>
<p>The details of each step are quite lengthy, and can be found in section
11 of the <a href="https://www.w3.org/TR/css-grid-1/#layout-algorithm">
CSS Grid Layout Module Level 1 documentation</a>.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch1-13-1">1.13. Table Layout</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>The layout of tables can get quite complicated, especially because CSS
defines two different ways to calculate table and cell widths, as well
as two ways to handle the borders of tables and elements internal to the
table. Figure 1-6 illustrates the components of a table.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ 07. Table layout components ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p align="center">
<img class="displayed"
  src="/images/image007.png?raw=true"
  title="Table layout components"
  alt="Table layout components."
  style="width:50%;" />
</p>
<p align="center"><i>Figure 1-6. Table layout components</i></p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h4>Table Arrangement Rules</h4>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>In general, a table is laid out according to the following principles:</p>
<ul>
  <li>Each row box encompasses a single row of grid cells. All of the row
    boxes in a table fill the table from top to bottom in the order they
    occur in the source document. Thus, the table contains as many grid
    rows as there are row elements.</li>
  <li>A row group's box encompasses the same grid cells as the row boxes
    that it contains.</li>
  <li>A column box encompasses one or more columns of grid cells. Column
    boxes are placed next to each other in the order in which they
    occur. The first column box is on the left for left-to-right
    languages and on the right for rightto-left languages.</li>
  <li>A column group's box encompasses the same grid cells as the column
    boxes that it contains.</li>
  <li>Although cells may span several rows or columns, CSS does not define
    how that happens. It is instead left to the document language to
    define spanning. Each spanned cell is a rectangular box one or more
    grid cells wide and high. The top row of this rectangle is in the
    row that is parent to the cell. The cell's rectangle must be as far
    to the left as possible in left-to-right languages, but it may not
    overlap any other cell box. It must also be to the right of all
    cells in the same row that appear earlier in the source document in
    a left-to-right language. In right-to-left languages, a spanned cell
    must be as far to the right as possible without overlapping other
    cells, and must be to the left of all cells in the same row that
    come after it in the document source.</li>
  <li>A cell's box cannot extend beyond the last row box of a table or row
    group. If the table structure causes this condition, the cell must
    be shortened until it fits within the table or row group that
    encloses it.</li>
</ul>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h4>Fixed Table Layout</h4>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>The fixed-layout model is fast because its layout doesn't depend on the
contents of table cells; it's driven by the width values of the table,
columns, and cells within the first row of the table. The fixed-layout
model uses the following steps:</p>
<ol type="1">
  <li>Any column element whose width property has a value other than auto
    sets the width for that column.</li>
  <li>If a column has an auto width, but the cell in the first row of the
    table within that column has a width other than auto, that cell sets
    the width for that column. If the cell spans multiple columns, the
    width is divided equally among the columns.</li>
  <li>Any columns that are still auto-sized are sized so that their widths
    are as equal as possible.</li>
</ol>
<p>At that point, the width of the table is set to be either the value of
width for the table or the sum of the column widths, whichever is
greater. If the table turns out to be wider than the column widths, the
difference is divided by the number of columns and added to each of
them.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h4>Automatic Table Layout</h4>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>The automatic-layout model, although not as fast as the fixedlayout
model, is likely to be much more familiar to authors, because it's
substantially the same model that HTML tables have used for years. In
most current user agents, use of this model will be triggered by a table
with a width of auto, regardless of the value of table-layout---although
this is not assured.</p>

<p>Here's how the model works:</p>
<ol type="1">
  <li>For each cell in a column, calculate both the minimum and maximum
    cell width.</li>
  <li>Determine the minimum width required to display the content. In
    determining the minimum content width, the content can flow to any
    number of lines, but it may not stick out of the cell's box. If the
    cell's width value is larger than the minimum possible width, the
    minimum cell width is set to that value. If the cell's width value
    is auto, the minimum cell width is set to the minimum content width.</li>
  <li>For the maximum width, determine the width required to display the
    content without any line-breaking, other than that forced by
    explicit line-breaking (e.g., due to the &lt;br&gt; element). That value
    is the maximum cell width.</li>
  <li>For each column, calculate both the minimum and maximum column width:
    <ol type-="a">
      <li>The column's minimum width is determined by the largest minimum cell width of the 
	    cells within the column. If the column has been given an explicit width value that is 
		larger than any of the minimum cell widths within the column, the minimum column width 
		is set to the value of width.</li>
      <li>For the maximum width, take the largest maximum cell width of the cells within the column. 
	    If the column has an explicit width value larger than any of the maximum cell widths within 
		the column, the maximum column width is set to the value of width. These two behaviors recreate 
		the traditional HTML table behavior of forcibly expanding any column to be as wide as its widest
        cell.</li>
      <li>In cases where a cell spans more than one column, the sum of the minimum column widths must 
	    be equal to the minimum cell width for the spanning cell. Similarly, the sum of the maximum 
		column widths must equal the spanning cell's maximum width. User agents should divide any 
		changes in column widths equally among the spanned columns.</li>
    </ol>
  </li>
</ol>
<p>In addition, the user agent must take into account that when a column
width has a percentage value for its width, the percentage is calculated
in relation to the width of the table---even though that width is not
known yet. The user agent must hang on to the percentage value and use
it in the next part of the algorithm. Once the user agent has determined
how wide or narrow each column can be, it can calculate the width of the
table. This happens as follows:</p>
<ol type="1">
  <li>If the computed width of the table is not auto, the computed table
    width is compared to the sum of all the column widths plus any
    borders and cell spacing. (Columns with percentage widths are likely
    calculated at this time.) The larger of the two values is the final
    width of the table. If the table's computed width is larger than the
    sum of the column widths, borders, and cell spacing, all columns are
    increased in width by an equal amount so they fill the computed
    width of the table.</li>
  <li>If the computed width of the table is auto, the final width of the
    table is determined by summing up the column widths, borders, and
    cell spacing. This means the table will be only as wide as needed to
    display its content, just as with traditional HTML tables. Any
    columns with percentage widths use that percentage as a constraint,
    but it is a constraint that a user agent does not have to satisfy.</li>
</ol>
<p>Once the last step is completed (and only then), the user agent can
actually lay out the table.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h4>Collapsing Cell Borders</h4>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>The collapsing cell model largely describes how HTML tables have always
been laid out when they have no cell spacing. The following rules govern
this model:</p>
<ul>
  <li>Table elements cannot have any padding, although they can have
    margins. Thus, there is never separation between the border around
    the outside of the table and its outermost cells.</li>
  <li>Borders can be applied to cells, rows, row groups, columns, and
    column groups. The table element itself can, as always, have a
    border.</li>
  <li>There is never any separation between cell borders. In fact, borders
    collapse into each other where they adjoin so that only one of the
    collapsing borders is actually drawn. This is somewhat akin to
    margin collapsing, where the largest margin wins. When cell borders
    collapse, the "most interesting" border wins.</li>
  <li>Once they are collapsed, the borders between cells are centered on
    the hypothetical grid lines between the cells.</li>
</ul>
<h5>Collapsing borders</h5>
<p>When two or more borders are adjacent, they collapse into each other, as
shown in Figure 1-7. There are strict rules governing which borders will
win and which will not:</p>
<ol type="1">
  <li>If one of the collapsing borders has a border-style of hidden, it
    takes precedence over all other collapsing borders: all borders at
    this location are hidden.</li>
  <li>If one of the collapsing borders has a border-style of none, it
    takes the lowest priority. There will be no border drawn at this
    location only if all of the borders meeting at this location have a
    value of none. Note that none is the default value for border-style.</li>
  <li>If at least one of the collapsing borders has a value other than
    either none or hidden, narrow borders lose out to wider ones. If two
    or more of the collapsing borders have the same width, the border
    style is taken in the following order, from most preferred to least:
    double, solid, dashed, dotted, ridge, outset, groove, inset. Thus,
    if two borders with the same width collapse and one is dashed while
    the other is outset, the border at that location will be dashed.</li>
  <li>If collapsing borders have the same style and width but differ in
    color, the color used is taken from an element in the following
    list, from most preferred to least: cell, row, row group, column,
    column group, table. Thus, if the borders of a cell and a
    column---identical in every way except color---collapse, the cell's
    border color (and style and width) will be used. If the collapsing
    borders come from the same type of element---such as two row borders
    with the same style and width, but different colors---the one
    farthest to the left and top wins in left-to-right languages; in
    right-to-left languages, the cell farthest to the right and top wins.</li>
</ol>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ 08. Collapsing cell borders model ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p align="center">
<img class="displayed"
  src="/images/image008.png?raw=true"
  title="Collapsing cell borders model"
  alt="Collapsing cell borders model."
  style="width:50%;" />
</p>
<p align="center"><i>Figure 1-7. Collapsing cell borders model</i></p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>Vertical Alignment Within Cells</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>The following describes the detailed process for aligning cell contents
within a row:</p>
<ol type="1">
  <li>If any of the cells are baseline-aligned, the row's baseline is
    determined and the content of the baseline-aligned cells is placed.</li>
  <li>Any top-aligned cell has its content placed. The row now has a
    provisional height, which is defined by the lowest cell bottom of
    the cells that have already had their content placed.</li>
  <li>If any remaining cells are middle- or bottom-aligned, and the
    content height is taller than the provisional row height, the height
    of the row is increased by lowering the baseline in order to enclose
    the tallest of those cells.</li>
  <li>All remaining cells have their content placed. In any cell with
    contents shorter than the row height, the cell's padding is
    increased in order to match the height of the row.</li>
</ol>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h2 id="ch2">2. CHAPTER 2 Values</h2>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>There are a variety of value types in CSS, most of which use units.
Combining basic value types (such as numbers) with units (such as
pixels) makes it possible to do any number of interesting things with
CSS.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch2-1-1">2.1. Keywords</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>Keywords are defined on a per-property basis and have a meaning specific
only to a given property. For example, normal has totally unique
meanings for the properties font-variant and letter-spacing. Keywords,
like property names, are not case-sensitive.</p>

<p>CSS defines three "global" keywords that are accepted by every property
in the specification: inherit</p>

<p>Forces the value for the property to be inherited from the element's
parent element, even if the property in question is not inherited
(e.g., background-image). Another way to think of this is that the
value is copied from the parent element.</p>

<h5>initial</h5>

<p>Forces the value of the property to be the initial value defined by
the relevant CSS module. For example, fontstyle: initial sets the
value of font-style to normal regardless of the font-style value that
would have been inherited from the parent element. In cases where the
initial value is defined as determined by the user agent, such as for
font-size, the value is set to the "default" defined by the user
agent's preferences.</p>

<h5>unset</h5>

<p>Combines the effects of both inherit and initial, with a rudimentary
logic built in for good measure. If a property is inherited (e.g.,
color), then unset has the same effect as inherit. If the property is
<i>not</i> inherited (e.g., backgroundimage), then unset has the same
effect as initial.</p>

<p>If you have a situation where you want to set all of the properties on
an element to their default values, thus breaking any chains of
inheritance, see the all property in Chapter 4.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch2-2-1">2.2. Color Values</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>Color values can be expressed in a variety of ways:</p>

<h5><i>#RRGGBB</i></h5>

<p>This is a hex-pair notation familiar to authors using traditional
HTML. In this format, the first pair of digits corresponds to the red
level, the second pair to the green, and the third pair to the blue.
Each pair is in hexadecimal notation in the range 00--FF (decimal
0--255). Thus, a "pure" blue is written #0000FF, a "pure" red is
written #FF0000, and so on.</p>

<h5><i>#RGB</i></h5>

<p>This is a shorter form of the six-digit notation described previously.
In this format, each digit is replicated to arrive at an equivalent
six-digit value; thus, #F8C becomes #FF88CC.</p>

<h5><i>#RRGGBBAA</i></h5>

<p>An extension of the #RRGGBB notation which adds an alpha channel. As
with the R, G, and B values, the A (alpha) value is in hexadecimal
notation in the range 00-- FF. These are mapped from hexadecimal to
decimal in the range 0--1; thus, #00FF0099 is equivalent to the color
#00FF00 (light green) with an opacity of 0.6. The opacity here is
derived by converting hexadecimal 99 to decimal 153, and then dividing
153 by 255 to get 0.6. Put another way, #00FF0099 is exactly
equivalent to rgba(0,255,0,0.6). Note: support for this notation first
emerged in early 2016.</p>

<h5><i>#RGBA</i></h5>

<p>This is a shorter form of the eight-digit #RRGGBBAA notation described
previously. In this format, each digit is replicated to arrive at an
equivalent eight-digit value; thus,</p>

<p>&pound;F8C6 becomes #FF88CC66. Note: support for this notation first emerged in early 2016.</p>

<h5><i>rgb(rrr,ggg,bbb)</i></h5>

<p>This format allows the author to use RGB values in the range 0--255;
only integers are permitted. Not coincidentally, this range is the
decimal equivalent of 00--FF in hexadecimal. In this format, "pure"
green is rgb(0,255,0), and white is represented as rgb(255,255,255).</p>

<h5><i>rgb(rrr.rr%,ggg.gg%,bbb.bb%)</i></h5>

<p>This format allows the author to use RGB values in the range 0% to
100%, with decimal values allowed (e.g., 75.5%). The value for black
is thus rgb(0%,0%,0%), whereas "pure" blue is rgb(0%,0%,100%).</p>

<h5><i>hsl(hhh.hh,sss.ss%,lll.ll%)</i></h5>

<p>This format permits authors to specify a color by its hue angle,
saturation, and lightness (HSL). The hue angle is always a unitless
number or a <i>&lt;degree&gt;</i> value in the range 0 to 360, and the
saturation and brightness values are always percentages. Hue angles 0
and 360 are equivalent, and are both red. Hue angles greater than 360
can be declared, but they are normalized to the 0--360 range; thus, setting a
hue angle of 454 is equivalent to setting an angle of 94.</p>

<p>Any HSL value, regardless of color angle, will be rendered as a shade of gray if the
saturation value is 0%; the exact shade will depend on the lightness
value. Any HSL value, regardless of the hue angle, will be rendered
solid black if lightness is 0% and solid white if lightness is 100%. The
"normal" lightness value---that is, the value associated with most
common colors---is 50%. <i>rgba(rrr,ggg,bbb,a.aa) rgba(rrr.rr%,ggg.gg%,bbb.bb%,a.aa) hsla(hhh.hh,sss.ss%,lll.ll%,a.aa)</i></p>

<p>These extend the previous three formats to include an alpha (opacity)
value. The alpha value must be a real number between 0 and 1
inclusive; percentages are not permitted for the alpha value. Thus,
rgba(255,0,0,0.5) and rgba(100%,0%,0%,0.5) and hsla(0,100%,50%,0.5)
are all equivalent half-opaque red.</p>

<h5><i>&lt;keyword&gt;</i></h5>

<p>One of 16 recognized keywords based on the original Windows VGA
colors. These keywords are aqua, black, blue, fuchsia, gray, green,
lime, maroon, navy, olive, purple, red, silver, teal, white, and
yellow. Browsers generally also recognize the 148 color keywords
documented in the [CSS Color Module Level 4
specification](http://www.w3.org/TR/css-color-4/), referred to for
historical reasons as "the X11 colors" (though the list does not
precisely replicate X11's colors).</p>

<h5>currentColor</h5>

<p>A special keyword that represents the current computed value of the
element's color property. This means you can declare background-color:
currentColor and set the element's background to be the same color as
its foreground (not recommended). When applied to the color property,
it is equivalent to declaring color: inherit. It can also be used on
borders; border: 1px solid is equivalent to border: 1px solid
currentColor. This can be quite useful when (un)setting a border's
color via DOM scripting.</p>

<h5>transparent</h5>

<p>A special keyword that is (just barely) a shorthand for rgba(0,0,0,0),
which is the computed value any time transparent is used.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch2-3-1">2.3. Number Values</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>A number value is expressed as a positive or negative number (when permitted). Numbers 
can be either real (represented as <i>&lt;number&gt;</i>) or integers (<i>&lt;integer&gt;</i>). 
They may also restrict the range of acceptable values, as with color values that accept only 
integers in the range 0--255. A more common range restriction is to limit a number to be 
non-negative. These are sometimes represented as <i>&lt;non-negative number&gt;</i> or 
<i>&lt;non-negative integer&gt;</i>.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch2-4-1">2.4. Percentage Values</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>A percentage value is expressed as a <i>&lt;number&gt;</i> followed immediately by a percent 
sign (%). There should never be any space between the number and the percent sign. A percentage 
value will always be computed relative to something else. For example, declaring font-size: 120% 
for an element sets its font size to 120% of the computed font-size of its parent element. 
Fractional values, such as 543.21%, are valid. Some properties may restrict percentage values to 
be non-negative.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch2-5-1">2.5. Length Values</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>A length value is expressed as a positive or negative number (when permitted), followed 
immediately by a unit identifier. There should never be any space between the number and the 
unit identifier. A length value of 0 (zero) does not require a unit identifier.</p>

<h5><b>Number Values</b></h5>
<p>Length units are divided into two types: <i>absolute units</i>, which are (in theory) always 
measured in the same way, and <i>relative units</i>, which are measured in relation to other 
things. <b>Absolute Length Units</b></p>

<p>The available absolute units are:</p>

<h5><i>Centimeters</i> (cm)</h5>

<p>The centimeters found on rulers the world over. There are 2.54 centimeters to an inch, and 
1 centimeter equals 0.394 inches. The same mapping warnings that applied to inches also apply 
to centimeters.</p>

<h5><i>Millimeters</i> (mm)</h5>

<p>There are 10 millimeters to a centimeter, so you get 25.4 millimeters to an inch, and 1 
millimeter equals 0.0394 inches. Bear in mind the previous warnings about mapping lengths 
to displays.</p>

<h5><i>Quarter-millimeters</i> (q)</h5>

<p>Exactly what they say they are: one-fourth of a millimeter.</p>

<p>In other words, 4q equals one millimeter, and 400q equals one centimeter. Again, bear in mind 
the previous mapping warnings.</p>

<h5><i>Inches</i> (in)</h5>

<p>As you might expect, the same inches found on typical US rulers. The mapping from inches to a 
display device is usually approximate at best, because many systems have no concept of the 
relation of their display areas to "realworld" measurements such as inches. Thus, inches should 
be used with extreme caution in screen design.</p>

<h5><i>Points</i> (pt)</h5>

<p>Points are standard typographical measures used by printers and typesetters for centuries and 
by word-processing programs for decades. By modern definition, there are 72 points to an inch. 
Therefore, the capital letters of text set to 12 points should be 1/6 of an inch tall. For example, 
p {font-size: 18pt;} is equivalent to p {font-size: 0.25in;}, assuming proper mapping of lengths to 
the display environment (see previous comments).</p>

<h5><i>Picas</i> (pc)</h5>

<p>Another typographical term. A pica is equivalent to 12 points, which means there are 6 picas to 
an inch. The capital letters of text set to 1 pica should be 1/6 of an inch tall. For example, p 
{font-size: 1.5pc;} would set text to be the same size as the example declarations found in the 
definition of points. Keep in mind the previous warnings. <b>Relative Length Units</b></p>

<p>The available relative units are:</p>

<h5><i>Em-height</i> (em)</h5>

<p>This refers to the em-height of a given font face. In CSS, the em-height is equivalent to the 
height of the character box for the font face, which is to say the computed value of font-size. 
Ems can be used to set relative sizes for fonts; for example, font-size: 1.2em is the same as 
saying fontsize: 120%.</p>

<h5><i>Root element em-height</i> (rem)</h5>

<p>Equal to the em-height of the root element (in HTML, the html element).</p>

<h5><i>X-height</i> (ex)</h5>

<p>This refers to the x-height of the font face, which is to say the height of the lowercase "x" 
character in the given font face. However, the vast majority of font faces do not include their 
x-height, so many browsers approximate it (poorly) by simply setting 1ex to be equal to 0.5em.</p>

<h5><i>ZERO width</i> (ch)</h5>

<p>This refers to the width of a single zero (Unicode U+0300, "ZERO") in the current font family 
and size. This is often, but erroneously, assumed to mean "one character." This will only be true 
in monospace fonts, where all characters are the same width.</p>

<h5><b>Length Values</b></h5>
<p>Since most proportional fonts have zeros that are slimmer than the alphabetic symbols, setting 
something like width: 60ch will often result in lines of text with fewer than 60 characters.</p>

<h5><i>Pixels</i> (px)</h5>

<p>A pixel is usually thought of as a small box on a display, but CSS defines pixels more 
abstractly. In CSS terms, a pixel is defined to be about the size required to yield 96 units 
per inch. Many user agents ignore this definition in favor of simply addressing the pixels 
on the display, but others (such as those on high-resolution mobile devices) go the CSS 
route, treating each px as being multiple physical on-screen pixels.</p>

<h5><i>Viewport width unit</i> (vw)</h5>

<p>This unit is calculated with respect to the viewport's width, which is divided by 100. If the 
viewport is 937 pixels wide, for example, 1vw is equal to 9.37px. If the viewport's width changes, 
say by dragging the browser window to be wider or narrower, the value of vw changes along with it.</p>

<h5><i>Viewport height unit</i> (vh)</h5>

<p>This unit is calculated with respect to the viewport's height, which is divided by 100. If 
the viewport is 650 pixels tall, for example, 1vh is equal to 6.5px. If the viewport's height 
changes, say by dragging the browser window to be taller or shorter, the value of vh changes 
along with it.</p>

<h5><i>Viewport minimum unit</i> (vmin)</h5>

<p>This unit is 1/100 of the viewport's width or height, whichever is <i>lesser</i>. Thus, 
given a viewport that is 937 pixels wide by 650 pixels tall, 1vmin is equal to 6.5px.</p>

<h5><i>Viewport maximum unit</i> (vmax)</h5>

<p>This unit is 1/100 of the viewport's width or height, whichever is <i>greater</i>. Thus, 
given a viewport that is 937 pixels wide by 650 pixels tall, 1vmax is equal to 9.37px.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch2-6-1">2.6. Fraction Values</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>A <i>fraction value</i> is a <i>&lt;number&gt;</i> followed by the label fr. Thus, one
fraction unit is 1fr, four fraction units are 4fr, and so on. This is a concept introduced 
by Grid Layout, and is used to divide up fractions of the unconstrained space in a layout. 
Note that fr is <i>not</i> a <i>&lt;length&gt;</i> unit, and thus cannot be used in places 
where length values are permitted (e.g., calc() expressions, see "Calculation Values" on
page 45).</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch2-7-1">2.7. URIs</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>A URI value (<i>&lt;uri&gt;</i>) is a reference to a file such as a graphic or another 
stylesheet. CSS defines a URI as relative to the stylesheet that contains it. URI stands 
for Uniform Resource Identifier, which is the more recent name for URLs. (Technically, 
URLs are a subset of URIs.) In CSS, which was first defined when URIs were still called 
URLs, this means that references to URIs will often appear in the form url(<i>&lt;uri&gt;</i>). Fun!</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch2-8-1">2.8. Angles</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>The format of an <i>&lt;angle&gt;</i> is expressed as a <i>&lt;number&gt;</i> followed 
immediately by an angle unit. There are four types of angle units: degrees (deg), grads (grad), 
radians (rad), and turns (turn). For example, a right angle could be declared as 90deg, 100grad, 
1.571rad, or 0.25turn. In each case, the values are translated into degrees in the range 0 
through 360. This is also true of negative values: −90deg is equivalent to 270deg.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch2-9-1">2.9. Times</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>A time value (<i>&lt;time&gt;</i>) is expressed as a <i>&lt;number&gt;</i> followed
immediately by a time unit. There are two types of time units: seconds (s) and milliseconds 
(ms). Time values appear in aural styles, which are not widely supported, and in the much 
better supported transitions and animations.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch2-10-1">2.10. Frequencies</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>A frequency value (<i>&lt;frequency&gt;</i>) is expressed as a non-negative 
<i>&lt;number&gt;</i> followed immediately by a frequency unit. There are two types of 
frequency units: hertz (Hz) and kilohertz (kHz).</p>

<p>The unit identifiers are case-insensitive, so 6kHz and 6khz are equivalent. As of this 
writing, frequency values are only used with aural styles, which are not well supported.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch2-11-1">2.11. Position</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>A position value (<i>&lt;position&gt;</i>) is how you specify the placement of an
origin image in backgrounds, object fitting, masking placement, and a few other 
circumstances. Its syntactical structure is rather complicated:</p>

<pre>
&lbrack;
&lbrack; left &vert; center &vert; right &vert; top &vert; bottom &vert; <i>&lt;percentage&gt;</i> &vert; <i>&lt;length&gt;</i> &rbrack; &vert;
&lbrack; left &vert; center &vert; right &vert; <i>&lt;percentage&gt;</i> &vert; <i>&lt;length&gt;</i> &rbrack;
&lbrack; top &vert; center &vert; bottom &vert; <i>&lt;percentage&gt;</i> &vert; <i>&lt;length&gt;</i> &rbrack; &vert;
&lbrack; center &vert; &lbrack; left &vert; right &rbrack; &lbrack; <i>&lt;percentage&gt;</i> &vert; <i>&lt;length&gt;</i> &rbrack;? &rbrack; &&
&lbrack; center &vert; &lbrack; top &vert; bottom &rbrack; &lbrack; <i>&lt;percentage&gt;</i> &vert; <i>&lt;length&gt;</i> &rbrack;? &rbrack;
&rbrack;
</pre>

<p>That might seem a little convoluted and repetitive, but it's all down to the subtly 
complex patterns that this value type has to allow, such as center, bottom right, 50% 
center, left 77px, and so on. The notation used here is described in "Value Syntax 
Conventions" on page 73.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch2-12-1">2.12. Strings</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>A string (<i>&lt;string&gt;</i>) is a series of characters enclosed by either
single or double quotes. If a string needs to include the same quote
that encloses it, it must be escaped. For example,</p>

<p>&apos;That\&apos;s amazing!&apos; or &quot;Deploy the \&quot;scare quotes\&quot; at once!&quot;.
If a newline is needed within a string, it is represented as \A, which
is the Unicode codepoint for the line feed character. Any Unicode
character can be represented using an escaped codepoint reference; thus,
a left curly double quotation mark can be represented with \201C. If a
string does contain a line feed for legibility reasons, it must be
escaped and will be removed when processing the string.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch2-13-1">2.13. Identifiers</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>There are some properties that accept an <i>identifier value</i>, which is a
user-defined label of some kind; the most common examples are grid lines
and areas in grid layout and keyframe names in animations. Identifiers
are represented in the value syntax as <i>&lt;identifier&gt;</i>. Identifiers are
words and are case-sensitive; thus, myID and MyID are, as far as CSS is
concerned, completely distinct and unrelated to each other. In cases
where a property accepts both an identifier and one or more keywords,
the author should take care to never define an identifier identical to a
valid keyword.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch2-14-1">2.14. Attribute Values</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>In a few CSS properties, it's possible to pull in the value of an HTML
attribute defined for the element being styled. This is done with the
attr() value. As of early 2018, this is almost exclusively done with
generated content, using the content property.</p>

<p>For example, h2::before {content: &quot;&lbrack;&quot; attr(ID) &quot;&rbrack; &quot;;} will insert
an opening square bracket, the ID of the h2 element, and then a closing
square bracket and trailing space. Any attribute, including HTML data-&ast;
attributes, can be addressed in this manner.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch2-15-1">2.15. Calculation Values</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>Calculation values take the form calc(), with an equation inside the
parentheses. calc() can be used wherever <i>&lt;length&gt;</i>, <i>&lt;frequency&gt;</i>,
<i>&lt;angle&gt;</i>, <i>&lt;time&gt;</i>, <i>&lt;percentage&gt;</i>, <i>&lt;number&gt;</i>, or
<i>&lt;integer&gt;</i> values are allowed. You can also use all these units.</p>

<b>Identifiers</b>
<p>types within a calc() value, though there are some limitations to keep
in mind.</p>

<p>Inside the parentheses, you can construct simple mathematical
expressions. The permitted operators are + (addition), -- (subtraction),
&ast; (multiplcation), and / (division), as well as parentheses. These
follow the traditional PEMDAS (parentheses, exponents, multiplication,
division, addition, subtraction) precedence order---although in this
case it's really just PMDAS, since as of early 2018, exponents are not
permitted in calc().</p>

<p>The basic limitation is that calc() does simple type-checking to make
sure that units are compatible:</p>
<ol>
  <li>To either side of a + or -- operator, both values must have the same
    unit type or must both be <i>&lt;number&gt;</i> and/or <i>&lt;integer&gt;</i> values
    (in which case, the result is a <i>&lt;number&gt;</i>).</li>
  <li>Given a &ast; operator, one of the values involved must be a <i>&lt;number&gt;</i> 
    (which, remember, includes <i>&lt;integer&gt;</i> values).</li>
  <li>Given a / operator, the value on the <i>right</i> side must be a <i>&lt;number&gt;</i>. If 
    the left-side value is an <i>&lt;integer&gt;</i>, the result is a <i>&lt;number&gt;</i>. 
	Otherwise, the result is of the unit used on the left side.</li>
  <li>Any circumstance that creates division by zero makes the value invalid.</li>
</ol>
<p>There's one more notable limitation: whitespace is <i>required</i> to either
side of the + and - operators, while it is not for &ast; and /. This avoids
ambiguity with respect to numeric values, which can be negative.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch2-16-1">2.16. Variable Values</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>As this book was being finished in early 2018, a new capability was
being added to CSS. The technical term for this is <i>custom properties</i>,
even though what these really do is create (sort of) variables in your
CSS. They do not, contrary to their name, create special CSS properties,
in the sense of properties like color or font.</p>

<p>Custom properties are defined by giving a custom identifier a value, like this:</p>

<pre>
<b>html</b> {
  &dash;-mainColor: #AEA434;
}
</pre>

<p>The important thing is that any custom identifier of this type begins
with <i>two</i> hyphens (&dash;-). Anything else, and the identifier will not be
recognized, meaning the variable definition will fail.</p>

<p>The defined value can then be invoked later on using a var() value type, like this:</p>

<pre>
<b>h1</b> {<b>color</b>: var(&dash;-mainColor);}
</pre>
<p>Note that these names are case-sensitive, so &dash;-maincolor and
&dash;-MainColor are completely separate identifiers. Custom properties are
scoped to the element to which they are applied.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h2 id="ch3">3. CHAPTER 3 Selectors and Queries</h2>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch3-1-1">3.1. Selectors</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>Universal Selector</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>Universal Selector</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Pattern</b></td>
	  <td><p>&ast;</p></td>
	</tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Matches any element name in the document's language. If a rule does not have an 
	  explicit selector, the universal selector is inferred.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td><pre>&ast; {color: red }<br>div &ast; p {color: blue;}</pre></td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>Type Selector</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>Type Selector</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Pattern</b></td>
	  <td>element1</td>
	</tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Matches the name of an element in the document's language. Every instance of 
	  the element name is matched. (CSS1 referred to these as "element selectors.").</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td><pre>body {background: #FFF;} <br>p {font-size: 1em;}</pre></td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>Descendant Selector</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>Descendant Selector</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Pattern</b></td>
	  <td>element1 element2 ...</td>
	</tr>
	  <td><b>Description</b></td>
	  <td>Matches elements based on their status as a descendant of another element. The 
	  matched element can be a child, grandchild, great-grandchild, etc. of the ancestor 
	  element. (CSS1 referred to these as "contextual selectors.")</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
body h1 {font-size: 200%;} 
table tr td div ul li {color:purple;} element1 &gt; element2
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>Child Selector</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>Child Selector</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Pattern</b></td>
	  <td>element1 &gt; element2</td>
	</tr>
	  <td><b>Description</b></td>
	  <td>Matches an element based on its status as a child of another element. It is more 
	  restrictive than a descendant selector, as only a child will be matched.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
div &gt; p {color: cyan;}
ul &gt; li {font-weight: bold;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>Adjacent Sibling Selector</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>Adjacent Sibling Selector</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Pattern</b></td>
	  <td>element1 + element2</td>
	</tr>
	  <td><b>Description</b></td>
	  <td>Matches an element that is the following adjacent sibling of another element. (Sibling 
	  elements, as the name implies, share the same parent element.) Any anonymous text nodes 
	  between the two elements are ignored; only elements and their positions in the document 
	  tree are considered.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
table + p {margin-top: 2.5em;}
h1 + &ast; {margin-top: 0;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>General Sibling Selector</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>General Sibling Selector</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Pattern</b></td>
	  <td>element1 &#126; element2</td>
	</tr>
	  <td><b>Description</b></td>
	  <td>Matches an element that is a sibling of another element which it follows in the document 
	  tree. Any text or other elements between the two elements are ignored; only the elements and 
	  their positions in the document tree are considered.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
table + p {margin-top: 2.5em;}
h1 + &ast; {margin-top: 0;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>Class Selector</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>Class Selector</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Pattern</b></td>
	  <td>element1.classname<br>element1.classname1.classname2</td>
	</tr>
	  <td><b>Description</b></td>
	  <td>In languages that permit it, such as HTML, SVG, and MathML, a class 
	  selector using "dot notation" matches elements that have a class attribute containing a 
	  specific value or values. The name of the class value must immediately follow the dot. 
	  Multiple class values can be chained together. If no element name precedes the dot, the 
	  selector matches all elements bearing that class value or values.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
p.urgent {color: red;} 
a.external {font-style: italic;}    
.example {background: olive;}  
.note.caution {background: yellow;} 
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>ID Selector</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>ID Selector</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Pattern</b></td>
	  <td>element1#idname</td>
	</tr>
	  <td><b>Description</b></td>
	  <td>In languages that permit it, such as HTML or SVG, an ID selector selects elements 
	  that have an id attribute containing a specific value. The name of the ID value must 
	  immediately follow the octothorpe (#). If no element name precedes the octothorpe, the 
	  selector matches all elements containing that ID value.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
h1#page-title {font-size: 250%;}
body#home {background: silver;}
#example {background: lime;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>Selectors</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>Simple Attribute Selector</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>Simple Attribute Selector</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Pattern</b></td>
	  <td>element1&lbrack;attr&rbrack;</td>
	</tr>
	  <td><b>Description</b></td>
	  <td>Matches elements based on the presence of an attribute, regardless of the attribute's value.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
a&lbrack;rel&rbrack; {border-bottom: 3px double gray;}
p&lbrack;class&rbrack; {border: 1px dotted silver;} 
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>Exact Attribute Value Selector</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>Exact Attribute Value Selector</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Pattern</b></td>
	  <td>element1&lbrack;attr=&quot;value&quot;&rbrack;</td>
	</tr>
	  <td><b>Description</b></td>
	  <td>Matches elements based on the precise and complete value of an attribute.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
a&lbrack;rel=&quot;start&quot;&rbrack; {font-weight: bold;}
p&lbrack;class=&quot;urgent&quot;&rbrack; {color: red;} 
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>Partial Attribute Value Selector</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>Partial Attribute Value Selector</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Pattern</b></td>
	  <td>element1&lbrack;attr&#126;=&quot;value&quot;&rbrack;</td>
	</tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Matches elements based on a portion of the spaceseparated value of an attribute. Note that &lbrack;class&#126;=&quot;<i>value</i>&quot;&rbrack; is equivalent to <i>.value</i> (see above).</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
a&lbrack;rel&#126;=&quot;friend&quot;&rbrack; {text-transform: uppercase;}
p&lbrack;class&#126;=&quot;warning&quot;&rbrack; {background: yellow;} 
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>Beginning Substring Attribute Value Selector</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>Beginning Substring Attribute Value Selector</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Pattern</b></td>
	  <td>element1&lbrack;attr&#94;=&quot;substring&quot;&rbrack;</td>
	</tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Matches elements based on a substring at the very beginning of an attribute's value.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
a&lbrack;href&#94;=&quot;/blog&quot;&rbrack; {text-transform: uppercase;}
p&lbrack;class&#94;=&quot;test-&quot;&rbrack; {background: yellow;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>Ending Substring Attribute Value Selector</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>Ending Substring Attribute Value Selector</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Pattern</b></td>
	  <td>element1&lbrack;attr&dollar;=&quot;substring&quot;&rbrack;</td>
	</tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Matches elements based on a substring at the very end of an attribute's value.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
a&lbrack;href&dollar;=&quot;.pdf&quot;&rbrack; {font-style: italic;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>Arbitrary Substring Attribute Value Selector</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>Arbitrary Substring Attribute Value Selector</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Pattern</b></td>
	  <td>element1&lbrack;attr&ast;=&quot;substring&quot;&rbrack;</td>
	</tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Matches elements based on a substring found anywhere within an attribute's value.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
a&lbrack;href&ast;=&quot;oreilly.com&quot;&rbrack; {font-weight: bold;}
div&lbrack;class&ast;=&quot;port&quot;&rbrack; {border: 1px solid red;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>Language Attribute Selector</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>Language Attribute Selector</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Pattern</b></td>
	  <td>element1&lbrack;lang&vert;=&quot;language-identifier&quot;&rbrack;</td>
	</tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Matches elements with a lang attribute whose value is one of a hyphen-separated list 
	  of values, starting with the value provided in the selector. In an HTML document, the 
	  language of an element is determined by its lang attribute. If an element does not have 
	  one, its language is determined by the lang attribute of its nearest ancestor that does 
	  have one, or, lacking that, by the Content-Language HTTP header response field (or the 
	  respective meta http-equiv) for the document.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
html&lbrack;lang&vert;=&quot;tr&quot;&rbrack; {color: red;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch3-2-1">3.2. Structural Pseudo-Classes</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>Strictly speaking, all pseudo-classes (like all selectors) are structural: they 
are, after all, dependent on document structure in some fashion. What sets the 
pseudo-classes listed here apart is that they are intrinsically about patterns found 
in the structure of the document: for example, selecting every other paragraph or 
elements that are the last children of their parent element.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>:empty</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p><b>Applies to</b> Any element</p>
<p><b>Description</b>  Matches elements that have no child nodes---that is, no child elements <i>or</i> content nodes. Content nodes are defined as any text, whitespace, entity reference, or CDATA nodes. Thus, &lt;p&gt; &lt;/p&gt; is <i>not</i> empty because it has a single whitespace character inside it; nor is the element empty if that space is replaced with a newline. Note that this pseudo-class does <i>not</i> apply to empty elements such as &lt;br&gt;, &lt;img&gt;, &lt;input&gt;, and so on.</p>
<p><b>Examples</b></p>
<pre>
p:empty {padding: 1em; background: red;}
div:not(:empty) {border: 1px solid;<br>
  padding: 1ch;}
li:empty {display: none;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>:first-child</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<b>Applies to</b>     Any element
<p><b>Description</b>  Matches an element when it is the first child of  
another element. Thus, div:first-child will select  
any div that is the first child of another element, 
<i>not</i> the first child element of any div.   
<p><b>Examples</b></p>
<pre>
td:first-child {border-left: 1px solid;}
p:first-child {text-indent: 0; margin-top: 2em;}    
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>:first-of-type</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<b>Applies to</b> Any element
<p><b>Description</b> Matches an element when it is the first child of its
type, as compared to all its sibling elements. Thus, div:first-of-type
will select any div that is the first child div of another element.
<p><b>Examples</b></p>
<pre>
td:first-of-type {border-left: 1px dotted;}
h2:first-of-type {color: fuchsia;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>:lang</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<b>Applies to</b>     Any element with associated language-encoding  
    information.
<p><b>Description</b>  Matches elements based on their human-language 
  encoding. Such language information must be 
 contained within, or otherwise associated with, the 
 document---it cannot be assigned from CSS. The 
 handling of :lang is the same as for &vert;= attribute  
 selectors.  
<p><b>Examples</b></p>
<pre>
html:lang(en) {background: silver;} <br>
&ast;:lang(fr) {quotes: &apos;&#171;&apos; &apos;&#187;&apos;;}     
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>:last-child</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<b>Applies to</b>     Any element 
<p><b>Description</b>  Matches an element when it is the last child of  
 another element. Thus, div:last-child will select  
 any div that is the last child of another element, 
 <i>not</i> the last child element of any div. 
<p><b>Examples</b></p>
<pre>
td:last-child {border-right: 1px solid;}
p:last-child {margin-bottom: 2em;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>:last-of-type</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<b>Applies to</b> Any element
<p><b>Description</b> Matches an element when it is the last child of its
type, as compared to all its sibling elements. Thus, div:last-of-type
will select any div that is the last child div of another element.
<p><b>Examples</b></p> 

<pre>
td:last-of-type {border-right: 1px dotted;}
h2:last-of-type {color: fuchsia;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>:nth-child(<i>a</i>n±<i>b</i>)</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<b>Applies to</b>  Any element

<p><b>Description</b> Matches every <i>n</i>th child with the pattern of selection
defined by the formula <i>a</i>n±<i>b</i>, where <i>a</i> and <i>b</i> are <i>&lt;integer&gt;</i>s
and n represents an infinite series of integers, counting forward from
the first child. Thus, to select every fourth child of the body element,
starting with the first child, you would write body &gt;

&ast;:nth-child(4n+1). This will select the first, fifth, ninth,
fourteenth, and so on children of the body.

If you literally wish to select the fourth, eighth, twelfth, and so on
children, you can modify the selector to body &gt; &ast;:nth-child(4n). It
is also possible for <i>b</i> to be negative: body &gt; &ast;:nth-child(4n-- 1)
selects the third, seventh, eleventh, fifteenth, and so on children of
the body.

In place of the <i>a</i>n±<i>b</i> formula, there are two keywords permitted:
even and odd. These are equivalent to 2n and 2n+1, respectively.

<p><b>Examples</b></p>
<pre>
&ast;:nth-child(4n+1) {font-weight: bold;}
tbody tr:nth-child(odd) {background-color: #EEF;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>:nth-last-child(<i>a</i>n±<i>b</i>)</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<b>Applies to</b> Any element

<p><b>Description</b> Matches every </i>n</i>th child with the pattern of selection
defined by the formula <i>a</i>n±<i>b</i>, where <i>a</i> and <i>b</i> are <i>&lt;integer&gt;</i>s
and n represents an infinite series of integers, <i>counting backward from
the last child</i>. Thus, to select every fourth-to-last child of the body
element, starting with the last child, you would write body &gt;
&ast;:nth-last-child(4n+1). This is, in effect, the mirror image of :nth-child.
In place of the <i>a</i>n±<i>b</i> formula, there are two keywords permitted:
even and odd. These are equivalent to 2n and 2n+1, respectively.
<p><b>Examples</b></p>
<pre>
&ast;:nth-last-child(4n+1) {font-weight: bold;} 
tbody tr:nth-last-child(odd) { 
  background-color: #EEF;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>:nth-last-of-type(<i>a</i>n±<i>b</i>)</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<b>Applies to</b> Any element
<p><b>Description</b> Matches every <i>n</i>th child that is of the same type as
the element named, with the pattern of selection defined by the formula
<i>a</i>n±<i>b</i>, where <i>a</i> and <i>b</i> are <i>&lt;integer&gt;</i>s and n represents an
infinite series of integers, <i>counting backward from the last such
element</i>. Thus, to select every third-to-last paragraph (p) that is a
child of the body element, starting with the first such paragraph, you
would write body &gt; p:nthlast-of-type(3n+1). This holds true even if
other elements (e.g., lists, tables, or other elements) are interspersed
between the various paragraphs. In place of the <i>a</i>n±<i>b</i> formula, there
are two keywords permitted: even and odd. These are equivalent to 2n and
2n+1, respectively.
<p><b>Examples</b></p>
<pre>
td:nth-last-of-type(even) {
  background-color: #FCC;} 
img:nth-last-of-type(3n) {float: left;
  border: 2px solid;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>:nth-of-type(<i>a</i>n±<i>b</i>)</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<b>Applies to</b> Any element
<p><b>Description</b> Matches every <i>n</i>th child that is of the same type as
the element named, with the pattern of selection defined by the formula
<i>a</i>n±<i>b</i>, where <i>a</i> and <i>b</i> are <i>&lt;integer&gt;</i>s and n represents an
infinite series of integers, counting forward from the first such
element. Thus, to select every third paragraph (p) that is a child of
the body element, starting with the first such paragraph, you would
write body &gt; p:nth-oftype(3n+1). This will select the first, fourth,
seventh, tenth, and so on child paragraphs of the body. This holds
true even if other elements (e.g., lists, tables, or other elements)
are interspersed between the various paragraphs.
In place of the <i>a</i>n±<i>b</i> formula, there are two keywords permitted:
even and odd. These are equivalent to 2n and 2n+1, respectively.
<p><b>Examples</b></p>
<pre>
td:nth-of-type(even) {background-color: #FCC;}
img:nth-of-type(3n) {float: right;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>:only-child</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<b>Applies to</b> Any element
<p><b>Description</b> Matches an element that is the only child element of its
parent element. A common use case for this selector is to remove the
border from any linked image, assuming that image is the only element in
the link. Note that an element can be selected by :only-child even if it
has its own child or children. It must simply be the only child of its
parent.

<p><b>Examples</b></p>
<pre>
a img:only-child {border: 0;}
table div:only-child {margin: 5px;}
</pre>

Any element

<b>:</b>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>only-of-type</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<b>Applies to</b>

<p><b>Description</b> Matches an element that is the only child element of its
type of its parent element. Note that an element can be selected by
:only-of-type even if it has its own child or children of its own type
(such as divs within a div).
<p><b>Examples</b></p> 
<pre>
p em:only-of-type {font-weight: bold;} 
section article:only-of-type {margin: 2em 0 3em;} 
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>:root</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<b>Applies to</b> The root element

<p><b>Description</b> This matches the document's root element, which in <br>
HTML is always the html element. In SVG, it is the <br>
svg element. In XML formats, the root element can <br>
have any name; thus, a generic root-element selector <br>
is needed.

<p><b>Examples</b></p>
<pre>
:root {font: medium serif;}<br>
:root &gt; &ast; {margin: 1.5em 0;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch3-3-1">3.3. The Negation Pseudo-Class</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
There is but one pseudo-class that handles negation, but it is so unique
that it deserves its own subsection.

<b>:not(<i>e</i>)</b> 
<b>Applies to</b>  Any element 
<p><b>Description</b>  Matches every element that is <i>not</i> described by    
the simple selector <i>e</i>. For example, you can  
select every element that is not a paragraph by     
stating &ast;:not(p).  
More usefully, negation can be used within the 
context of descendant selectors. An example of this 
would be selecting every element within a table     
that is not a data cell using table &ast;:not(td).     
Another example would be selecting every element    
with an ID that is not search by using 
     
&lbrack;id&rbrack;:not(&lbrack;id=&quot;search&quot;&rbrack;). 
     
Note that there is one exception to the "simple     
selector" definition of <i>e</i>: it cannot be a 
negation pseudoclass itself. That is, it is 
impermissible to write :not(:not(div)).     

Because :not() is a pseudo-class, it can be chained 
with other pseudo-classes as well as with instances 
of itself. For example, to select any focused  
element that isn't an a element, use
&ast;:focus:not(a). To select any element that isn't   
either a paragraph or a section, use
&ast;:not(p):not(section).     
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>The Negation Pseudo-Class</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
As of early 2018, the "simple selector" restriction means that
grouped, descendant, and combined selectors are not permitted within
:not() expressions. This restriction is being loosened in CSS
Selectors Level 4.

<p><b>Examples</b></p>
<pre>
ul &ast;:not(li) {text-indent: 2em;}
&ast;:not(&lbrack;type=&quot;checkbox&quot;&rbrack;):not(&lbrack;type=&quot;radio&quot;&rbrack;) { 
  margin: 0 1em;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch3-4-1">3.4. Interaction Pseudo-Classes</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>The pseudo-classes listed here are all related to the user's interaction
with the document: whether styling different link states, highlighting
an element that's the target of a fragment identifier, or styling form
elements based on their being enabled or disabled.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>:active</h3>  
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<b>Applies to</b>     Any interaction element     
 <p><b>Description</b>  Matches an element during the period in which it is 
 being activated. The most common example is 
 clicking on a hyperlink in an HTML document: while  
 the mouse button is being held down, the link is    
 active. There are other ways to activate elements,  
 and other elements can in theory be activated, 
 although CSS doesn't define them.   
<p><b>Examples</b></p>
<pre>
a:active {color: red;}
&ast;:active {background: blue;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>:checked</h3> 
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<b>Applies to</b>    Any interaction element that has an on/off state    
<p><b>Description</b>  Matches any user interface element that has been
"toggled on," such as a checked checkbox or a
filled radio button. 
<p><b>Examples</b></p>
<pre>
input:checked {
 outline: 3px solid rgba(127,127,127,0.5);}
input&lbrack;type=&quot;checkbox&quot;&rbrack;:checked {
  box-shadow: red 0 0 5px;} 
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>:disabled</h3> 
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<b>Applies to</b>  Any interaction element     
<p><b>Description</b>  Matches user interface elements that are not able 
to accept user input because of language attributes 
or other nonpresentational means; for example, 
&lt;input type=&quot;text&quot; disabled&gt; in HTML5. Note 
that :disabled does <i>not</i> apply when an input     
element has simply been removed from the viewport 
with properties like position or display. 
<p><b>Example</b></p>
<pre>
input:disabled {opacity: 0.5;} 
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>:enabled</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<b>Applies to</b>     Any interaction element     
<p><b>Description</b>  Matches user interface elements that are able to    
accept user input and that can be set to "enabled"  
and "disabled" states through the markup language   
itself. This includes any form input element in     
(X)HTML, but does not include hyperlinks.   
<p><b>Example</b></p>
<pre>
input:enabled {background: #FCC;}   
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>:focus</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<b>Applies to</b>    Any interaction element     
<p><b>Description</b>  Matches an element during the period in which it 
 has focus. One example from HTML is an input box    
that has the text-input cursor within it such that  
when the user starts typing, text will be entered   
into that box. Other elements, such as hyperlinks,  
can also have focus; however, CSS does not define   
which elements may or may not have focus.   
<p><b>Examples</b></p>
<pre>
a:focus {outline: 1px dotted red;}
input:focus {background: yellow;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>:hover</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>:hover</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Applies to </b></td>
	  <td>Any interaction element</td>
	</tr>
	  <td><b>Description</b></td>
	  <td>Matches an element during the period in which it is being <i>hovered</i> over (when the user 
	  is designating an element without activating it). The most common example of this is moving 
	  the mouse pointer inside the boundaries of a hyperlink in an HTML document. Other elements 
	  can in theory be hovered over, although CSS doesn't define which ones.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
a&lbrack;href&rbrack;:hover {text-decoration: underline;}
p:hover {background: yellow;} 
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>:link</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200">:link<h3>:link</h3></th>
	</tr>
  </thead>
  <tbody>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>A hyperlink to a resource that has not been visited</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Matches a link to a URI that has not been visited; that is, the URI to which the link 
	  points does not appear in the user agent's history. This state is mutually exclusive with 
	  the :visited state.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
a:link {color: blue;} 
&ast;:link {text-decoration: underline;} 
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>:target</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>:target</h3></th>
	</tr>
  </thead>
  <tbody>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>Any elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Matches an element which is itself matched by the fragment identifier portion of the URI 
	  used to access the page. Thus, http://www.w3.org/TR/ css3-selectors/#target-pseudo would be 
	  matched by :target and would apply the declared  styles to any element with the id of 
	  target-pseudo. If that element was a paragraph, it would also be matched by p:target.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
:target {background: #EE0;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>:visited</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>:visited</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Applies to</b></td>
	  <td>A hyperlink to a resource that has already been visited</td>
	</tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Matches a link to a URI that has been visited; that is, the URI to which the link points 
	  appears in the user agent's history. This state is mutually exclusive with the :link state.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
a:visited {color: purple;}
&ast;:visited {color: gray;}  
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch3-5-1">3.5. Pseudo-Elements</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
In CSS1 and CSS2, pseudo-elements were preceded by single colons, just
as pseudo-classes were. In CSS3 and later, pseudoelements use double
colons to distinguish them from pseudoclasses. For historical reasons,
browsers will support both single and double colons on pseudo-elements,
but the doublecolon syntax is recommended.
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>::after</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<b>Generates</b>    A pseudo-element containing generated content
  placed after the content in the element 
<p><b>Description</b>  Inserts generated content at the end of an element's
  content. By default, the pseudo-element is inline, 
					   but this can be changed using the property display. 
<p><b>Examples</b></p>
<pre>
a.external:after {
  content: &quot; &quot; url(/icons/globe.gif);} 
p:after {content: &quot; &vert;; &quot;;} 
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>::before</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<b>Generates</b>   A pseudo-element containing generated content 
placed before the content in the element
<p><b>Description</b>  Inserts generated content at the beginning of an 
  element's content. By default, the pseudo-element is 
  inline, but this can be changed using the property display. 
<p><b>Examples</b></p>
<pre>
a&lbrack;href&rbrack;:before {content: &quot;&lbrack;LINK&rbrack; &quot;;} 
p:before {content: attr(class);} 
a&lbrack;rel&vert;;=&quot;met&quot;&rbrack;:after {content: &quot; &ast;&quot;;} 
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>::first-letter</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<b>Generates</b>    A pseudo-element that contains the first letter of an element.  
<p><b>Description</b>  Styles the first letter of an element. Any leading  
  punctuation should be styled along with the first   
  letter. Some languages have letter combinations     
  that should be treated as a single character, and a 
  user agent may apply the first letter style to 
  both. Prior to CSS2.1, ::first-letter could be 
  attached only to block-level elements. CSS2.1  
  expanded its scope to include elements with a  
  display value of block, list-item, table-cell, 
  table-caption, or inlineblock. There is a limited   
   set of properties that can apply to a first letter. 
<p><b>Examples</b></p>
<pre>
h1:first-letter {font-size: 166%;} 
p:first-letter {text-decoration: underline;} 
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>::first-line</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<b>Generates</b>   A pseudo-element that contains the first formatted 
 line of an element 
<p><b>Description</b>  Styles the first line of text in an element, regardless
  of how many or how few words may appear in that 
					   line. ::first-line can be attached only to blocklevel 
					   elements. There is a limited set of properties that can 
					   apply to a first line. 
<p><b>Example</b></p>
<pre>
p.lead:first-line {font-weight: bold;} 
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch3-6-1">3.6. Media Queries</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>With media queries, an author can define the media environment in which
a given stylesheet, or portion of a stylesheet, is used by the browser.
In the past, this was handled by setting media types with the media
attribute on link elements, or with the media descriptor on &#64;import
declarations. Media queries take this concept several steps further by
allowing authors to choose stylesheets based on the features of a given
media type.</p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>Basic Concepts</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<p>The placement of media queries will be very familiar to any author who
has ever set a media type. Here are two ways of applying an external
stylesheet when rendering the document on a color printer:</p>
<pre>
&lt;link href=&quot;print-color.css&quot; type=&quot;text/css&quot; media=&quot;print and
(color)&quot; rel=&quot;stylesheet&quot;&gt;
<br>
&#64;import url(print-color.css) print and (color);
</pre>
<p>Anywhere a media type can be used, a media query can be used. This means
that it is possible to list more than one query in a comma-separated list:</p>
<pre>
&lt;link href=&quot;print-color.css&quot; type=&quot;text/css&quot; media=&quot;print and
(color), projection and (color)&quot; rel=&quot;stylesheet&quot;&gt;
<br>
&#64;import url(print-color.css) print and (color), projection and
(color);
</pre>

In any situation where one of the media queries evaluates to true, the
associated stylesheet is applied. Thus, given the previous &#64;import,
<i>print-color.css</i> will be applied if rendering to a color printer or a
color projection environment. If printing on a black-and-white printer,
both queries will evaluate to false and <i>print-color.css</i> will not be
applied to the document. The same holds for any screen medium, a
grayscale projection environment, an aural media environment, and so
forth.

Each query is composed of a media type and one or more listed media
features. Each media feature is enclosed in parentheses, and multiple
features are linked with the and keyword. There are two logical keywords
in media queries: and

Links together two or more media features in such a way that all of
them must be true for the query to be true. For example, (color) and
(orientation: landscape) and (min-device-width: 800px) means that all
three conditions must be satisfied: if the media environment has
color, and is in landscape orientation, and the device's display is at
least 800 pixels wide, the stylesheet is used.

<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>not</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->

Negates the entire query so that if all of the conditions are true,
the stylesheet is <i>not</i> applied. For example, not

(color) and (orientation: landscape) and (mindevice-width: 800px)
means that if the three conditions are satisfied, the statement is
negated. Thus, if the media environment has color, and is in landscape
orientation, and the device's display is at least 800 pixels wide, the
stylesheet is <i>not</i> used. In all other cases, it will be used. Note
that the not keyword can only be used at the beginning of a media
query. It is <i>not</i> legal to write something like (color) and not
(min-device-width: 800px). In such cases, the query will be ignored.
Note also that browsers too old to understand media queries will
always skip a stylesheet whose media descriptor starts with not.

There is no or keyword for use within a given query, but the commas that
separate a list of queries serve the function of an or; that is, screen,
print means "apply if the media is screen or print." Thus, instead of
screen and (max-color: 2) or (monochrome), which is invalid and thus
ignored, you should write screen and (max-color: 2), screen and
(monochrome).

There is one more keyword, only, which is designed to create deliberate
backward incompatibility.
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>only</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
Used to hide a stylesheet from browsers too old to understand media
queries. For example, to apply a stylesheet in all media, but only in
those browsers that understand media queries, you would write
something like &#64;import url(new.css) only all. In browsers that do
understand media queries, the only keyword is ignored. Note that the
only keyword can be used only at the beginning of a media query.
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>Media Query Values</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
There are two new value types introduced by media queries, which (as of
early 2018) are not used in any other context:

<i>&lt;ratio&gt;</i>
A ratio value is two positive <i>&lt;integer&gt;</i> values separated by a
solidus (/) and optional whitespace. The first value refers to the
width, and the second to the height. Thus, to express a
width-to-height ratio of 16:9, you can write 16/9 or 16 / 9.

<i>&lt;resolution&gt;</i>
A resolution value is a positive <i>&lt;integer&gt;</i> followed by either of
the unit identifiers dpi or dpcm. As usual, whitespace is not
permitted between the <i>&lt;integer&gt;</i> and the identifier.
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>Media Features</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
As of early 2018, the available media features are as follows. Note that
their values cannot be negative: width, min-width, max-width

<i>Values: &lt;length&gt;</i>
Refers to the width of the display area of the user agent. In a
screen-media web browser, this is the width of the viewport plus any
scrollbars. In paged media, this is the width of the page box. Thus,
(minwidth: 850px) applies when the viewport is greater than 850 pixels
wide.
device-width, min-device-width, max-device-width

<i>Values: &lt;length&gt;</i>
Refers to the width of the complete rendering area of the output
device. In screen media, this is the width of the screen. In paged
media, this is the width of the page. Thus, (max-device-width: 1200px)
applies when the device's output area is less than 1,200 pixels wide.
height, min-height, max-height

<i>Values: &lt;length&gt;</i>
Refers to the height of the display area of the user agent. In a
screen-media web browser, this is the height of the viewport plus any
scrollbars. In paged media, this is the height of the page box. Thus,
(height: 567px) applies when the viewport's height is precisely 567
pixels tall.
device-height, min-device-height, max-device-height

<i>Values: &lt;length&gt;</i>
Refers to the height of the complete rendering area of the output
device. In screen media, this is the height of the screen. In paged
media, this is the height of the page. Thus, (max-device-height:
400px) applies when the device's output area is less than 400 pixels
tall.
aspect-ratio, min-aspect-ratio, max-aspect-ratio

<i>Values: &lt;ratio&gt;</i>
Refers to the ratio that results from comparing the width media
feature to the height media feature (see the definition of
<i>&lt;ratio&gt;</i>). Thus, (min-aspect-ratio: 2/1) applies to any viewport
whose width-to-height ratio is at least 2:1.
device-aspect-ratio, min-device-aspect-ratio, max-deviceaspect-ratio

<i>Values: &lt;length&gt;</i>
Refers to the ratio that results from comparing the device-width media
feature to the device-height media feature (see the definition of
<i>&lt;ratio&gt;</i>). Thus, (device-aspect-ratio: 16/9) applies to any output
device whose display area width-to-height ratio is exactly 16:9.
color, min-color, max-color

<i>Values: &lt;integer&gt;</i>
Refers to the presence of color-display capability in the output
device, with an optional number representing the number of bits used
in each color component. Thus, (color) applies to any device with any
color depth at all, whereas (min-color: 4) means there must be at
least four bits used per color component. Any device that does not
support color will return 0.
color-index, min-color-index, max-color-index

<i>Values: &lt;integer&gt;</i>
Refers to the total number of colors available in the output device's
color lookup table. Thus, (min-colorindex: 256) applies to any device
with a minimum of 256 colors available. Any device that does not use a
color lookup table will return 0.

monochrome, min-monochrome, max-monochrome

<i>Values: &lt;integer&gt;</i>
Refers to the presence of a monochrome display, with an optional
number of bits per pixel in the output device's frame buffer. Thus,
(monochrome) applies to any monochrome output device, whereas
(minmonochrome: 2) applies to any monochrome output device with a
minimum of two bits per pixel in the frame buffer. Any device that is
not monochrome will return 0.

resolution, min-resolution, max-resolution

<i>Values: &lt;resolution&gt;</i>
Refers to the resolution of the output device in terms of pixel
density, measured in either dots per inch (dpi) or dots per centimeter
(dpcm). If an output device has pixels that are not square, the least
dense axis is used; for example, if a device is 100dpcm along one axis
and 120dpcm along the other, 100dpcm is the value returned.
Additionally, a bare resolution feature query can never match (though
min-resolution and max-resolution can).
orientation

<i>Values:</i> portrait <i>&vert;</i> landscape
Refers to the output device's total output area, where portrait is
returned if the media feature height is equal to or greater than the
media feature width. Otherwise, the result is landscape.
scan

<i>Values:</i> progressive <i>&vert;</i> interlace
Refers to the scanning process used in an output device with a media
type of tv.

grid

<i>Values:</i> 0 <i>&vert;</i> 1
Refers to the presence (or absence) of a grid-based output device,
such as a tty terminal. A grid-based device will return 1; otherwise,
0 is returned.

<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch3-7-1">3.7. Feature Queries</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
A <i>feature query</i> is an at-rule block similar to a media query. The
difference is that it queries a user agent about its support for a given
property-value combination. If the user agent indicates it supports the
query, the rules within the at-block are applied.
Otherwise, they are ignored.
A basic example is to ask the browser if it supports backgroundcolor:
red:
<b>&#64;supports</b> (<b>background-color</b>: red) { <b>html</b>
{<b>background-color</b>: yellow;} <b>body</b> {<b>background-color</b>:
white;} }
There is no obligation to use the property-value combination in the
query in the subsequent rules. In fact, there's no obligation even to
use the property that was part of the feature query. You can ask if a
browser supports color: #FFF and then write rules that never touch
color. (But just because you can doesn't mean you should.)
Feature queries are useful when applying advanced CSS features. For
example, converting a float-based layout to grid might look something
like this:
&lbrack;..<b>.float</b> <b>layout</b> <b>rules</b> <b>here</b>...&rbrack;
<b>&#64;supports</b> (<b>display</b>: grid) {
&lbrack;..<b>.grid</b> <b>layout</b> <b>rules</b> <b>here</b>...&rbrack;
&lbrack;..<b>.rules</b> <b>that</b> <b>turn</b> <b>off</b> <b>margins</b>, <b>clearing</b>,
<b>and</b> <b>other</b> <b>rules</b> <b>needed</b> <b>for</b> <b>float</b> <b>layout</b>
<b>but</b> <b>not</b> <b>in</b> <b>grid</b> <b>layout</b>...&rbrack; }
It's also possible to do a negated feature query using the keyword not:
<b>&#64;supports</b> <b>not</b> (<b>shape-outside</b>: circle()) {
&lbrack;..<b>.rules</b> <b>for</b> <b>use</b> <b>in</b> <b>browsers</b> <b>that</b>
<b>don</b>&apos;<b>t</b> <b>understand</b>
<b>circle</b> <b>float</b> <b>shapes</b>...&rbrack; }
<b>Feature Queries</b>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h2 id="ch4">4. CHAPTER 4 Property Reference</h2>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch4-1-1">4.1. Inheritance and Animation</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
Each property listed in this chapter has "Inh." and "Anim." values. The
values "N" (for no) and "Y" (for yes) indicate whether a property is
<i>inherited</i> by descendant elements and whether the property is
<i>animatable</i>, or able to be affected using the various animation and
transition properties. In cases where only some of a property's values
are animatable, the value given will be "P" (for partial) and more
details will be given in the property's definition.
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch4-2-1">4.2. Value Syntax Conventions</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
Any words presented in constant width are keywords that must appear
literally, without quotes. The forward slash (/) and the comma (,) must
also be used literally.

Any italicized words between "&lt;" and "&gt;" give a type of value, or a
reference to another property's values. For example, the property font
accepts values that originally belong to the property font-family. This
is denoted by using the text <i>&lt;fontfamily&gt;</i>. Similarly, if a value
type like a color is permitted, it will be represented using
<i>&lt;color&gt;</i>.

There are a number of ways to combine components of a value definition:

-   Two or more keywords strung together with only space separating them
    means that all of them must occur in the given order.

-   If a vertical bar separates alternatives (X &vert; Y), then any one of
    them must occur, but only one.

-   A vertical double bar (X ‖ Y) means that X, Y, or both must occur,
    but they may appear in any order.

-   A double ampersand (X && Y) means both X and Y must occur, though
    they may appear in any order. • Brackets (&lbrack;...&rbrack;) group things
    together. Thus "&lbrack;please ‖ help ‖ me&rbrack; do this" means that one or
    more of the words please, help, and me must appear (in any order,
    and at most once). do this must always appear, with those words in
    that order.

Every component or bracketed group may (or may not) be followed by one
of these modifiers:

-   An asterisk (&ast;) indicates that the preceding value or bracketed
    group is repeated zero or more times.

-   A plus (+) indicates that the preceding value or bracketed group is
    repeated one or more times.

-   An octothorp (#) indicates that the preceding value or bracketed
    group is repeated one or more times, separated by commas as needed.

-   A question mark (?) indicates that the preceding value or bracketed
    group is optional.

-   An exclamation point (!) indicates that the preceding value or
    bracketed group is required, and thus must result in at least one
    value, even if the syntax would seem to indicate otherwise.

-   A pair of numbers in curly braces ({M,N}) indicates that the
    preceding value or bracketed group is repeated at least M and at
    most N times.

<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch4-3-1">4.3. Universal Values</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
Any user agent that has fully implemented the Cascading and Inheritance
module will honor the following values for all properties. Think of it
as a given property's value syntax being written something like:

&lbrack; <i>(listed value syntax)</i> &rbrack; &vert; inherit &vert; initial &vert; unset

These three keywords are not listed in the following property
definitions, for purposes of clarity. The exception is the property all,
which accepts <i>only</i> these three keywords as values. For definitions of
these keywords' meaning, see Chapter 2.

<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3 id="ch4-4-1">4.4. Properties</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3><b>align-content</b>  <b>Inh. N Anim. N</b>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>align-content</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td><br>
	     <br>
	  </td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>See individual properties</td>
	</tr>
    <tr>
	  <td><b></b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b></b></td>
	  <td></td>
	</tr>
	  <td><b>Description</b></td>
	  <td>
	  </td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>

<b>Values</b>   flex-start &vert; flex-end &vert; center &vert; space-between &vert;<br>
space-around &vert; space-evenly &vert; stretch 
<b>Initial value</b>    stretch  
<b>Computed value</b>  As declared 
<b>Applies to</b>   Flex containers 
<b> Description</b>  Defines the distribution of flex lines along the cross<br>
     axis of a flex container, given that the container's<br>
     cross-axis length does not equal the sum of the flex<br>
     lines' size along the same axis. 
<p><b>Examples</b></p>
<pre>
  aside {display: flex; align-content: center;}<br>
  section {display: flex; height: 90vh;<br>
    align-content: flex-end;} 
</pre>
<b>Note</b>  As of early 2018, there are plans to have this prop-<br>
  erty apply to many (or all) elements, not just flex<br>
  flex containers, and be given the values start and end to replicate <br>
  replicate flex-start and flex-end behavior for <br>
  non-flex environments. Thanks to the center value,<br>
  this change would make vertical centering of con-<br>
  tent trivial in nearly all cases. 

<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3><b>align-items</b>  <b>Inh. N Anim. N</b>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>align-items</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td><br>
	     <br>
	  </td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>See individual properties</td>
	</tr>
    <tr>
	  <td><b></b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b></b></td>
	  <td></td>
	</tr>
	  <td><b>Description</b></td>
	  <td>
	  </td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>

<b>Values</b>    flex-start &vert; flex-end &vert; center &vert; baseline &vert; stretch 
<b>Initial value</b>  stretch 
<b>Computed value</b>   As declared 
<b>Applies to</b>     Flex containers, grid containers, and multicolumn containers  
<p><b>Description</b>  Sets a flex-container-wide default for items' 
alignment with respect to the cross axis of the
flex line they occupy. baseline alignment means the
items in a line are all placed such that the
baselines of their first lines of text line up. 
<p><b>Examples</b></p>
<pre>
div.flexy {align-items: flex-start;} 
section.gallery {align-items: baseline;} 
</pre>
<b>Note</b>  As of early 2018, there are plans to have this
property apply to many (or all) elements and be 
given the values start and end to replicate 
flex-start and flex-end behavior for non-flex 
environments. 
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3><b>align-self</b>  <b>Inh. N Anim. N</b></h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table>
  <thead>
    <tr>
	  <th>align-self</th>
	  <th>Inh. N Anim. N</th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>flex-start &vert; flex-end &vert; center &vert; baseline &vert;<br>
	  stretch</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>stretch</td>
	</tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declarede</td>
	</tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>Flex and grid items</td>
	</tr>
	  <td><b>Description</b></td>
	  <td>Sets the alignment for a single item with respect to the cross axis of the flex line it occupies.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
div.flexy .midpointed {align-self: center;}
section.gallery h1 {align-self: stretch;}
</pre>
      </td>
	<tr>
	  <td><b>Note</b></td>
	  <td>As of early 2018, there are plans to have this property apply to many (or all) elements, and be given the values start and end to replicate flex-start and flex-end behavior for non-flex environments.</td>
    </tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3><b>all</b>  <b>Inh. N Anim. N</b></h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>all</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Value</b></td>
	  <td>inherit &vert; initial &vert; unset</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>See individual properties</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Applies the declared value to all properties <i>except</i> direction and unicode-bidi, which are 
	  exempted for accessibility and historical reasons. This allows an author to, for example, force an 
	  element to reset all of its style properties to their default values, thus blocking the inheritance 
	  of values for all properties (except the exempted two).</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
&ast;.blendin {all: inherit;}
&ast;.embedded {all: unset;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3><b>animation</b>  <b>Inh. N Anim. N</b></h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>animation</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>&lbrack; <i>&lt;animation-name&gt;</i> ‖ <i>&lt;animation-duration&gt;</i> ‖<br>
<i>&lt;animation-timing-function&gt;</i> ‖ <i>&lt;animation-delay&gt;</i> ‖<br>
<i>&lt;animation-iteration-count&gt;</i> ‖ <i>&lt;animationdirection&gt;</i> ‖<br>
<i>&lt;animation-fill-mode&gt;</i> ‖ <i>&lt;animationplay-state&gt;</i> &rbrack;#</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>0s ease 0s 1 normal none running none</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements, ::before and ::after pseudoelements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>A shorthand property encompassing all the aspects of one or more comma-separated CSS animations. The parts of the value can occur in any order. Therefore, beware possible ambiguity in the delay and duration values. As of this writing, it is most likely that the first time value will be taken to define the duration and the second to define the delay, but this cannot be guaranteed.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
div#slide {animation: &apos;slide&apos; 2.5s linear
0 1 normal;}
h1 {animation: &apos;bounce&apos; 0.5s 0.33s ease-in-out infinite alternate;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>animation-delay Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>animation-delay</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td><i>&lt;time&gt;</i>&#35;</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>0s</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements, ::before and ::after pseudoelements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the amount of time that the user agent waits before starting the CSS animation(s). The timer starts when the user agent applies the animation CSS. For a noninteractive element, this is likely (but not guaranteed) to be at the end of page load.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
body {animation-delay: 1s, 2000ms, 4s;}
a:hover {animation-delay: 400ms;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!-- <h3>animation-direction Inh. N Anim. N</h3> -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>animation-direction</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>&lbrack; normal &vert; reverse &vert; alternate &vert; alternatereverse &rbrack;#</td>
	</tr>
	  <td><b>Initial value</b></td>
	  <td>normal</td>
    </tr>
	</tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	</tr>
	  <td><b>Applies to</b></td>
	  <td>All elements, ::before and ::after pseudoelements</td>
    </tr>
	</tr>
	  <td><b>Description</b></td>
	  <td>Specifies whether a CSS animation with more than one cycle (see animation-iteration-count) 
	  should always go the same direction or should reverse direction on every other cycle. For example, 
	  an alternate animation that moves an element 300 pixels to the right would move it 300 pixels to 
	  the left on every other cycle, thus returning it to its starting position. Setting that same 
	  animation to normal would cause the element to move 300 pixels right, then jump back to its 
	  starting place and move 300 pixels right again, over and over until the animation stops (assuming 
	  it ever does).</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
body
{animation-direction:
alternate, normal, normal;} #scanner {animation-direction: normal;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>animation-duration Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>animation-duration</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td><i>&lt;time&gt;</i>&#35;</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>0s</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements, ::before and ::after pseudoelements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the length of time it should take for each cycle of a CSS animation to run from 
	  start to finish. Therefore, in animations with only one cycle, it defines the total time of 
	  the animation. The default value, 0s, means that there will be no animation besides moving 
	  the element from its start state to its end state. Negative values are converted to 0s.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
h1 {animation-duration: 10s, 5s, 2.5s, 1250ms;}
.zip {animation-duration: 90ms;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!-- <h3>animation-iteration-count Inh. N Anim. N</h3> -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>animation-iteration-count</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>&lbrack; <i>&lt;number&gt;</i> &vert; infinite &rbrack;#</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>1</td>
    </tr>
	<tr>
	  <td><b>Computed As value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements, ::before and ::after pseudoelements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the number of cycles in the animation(s). The default value, 1, means that the 
	  animation will run exactly once, going from the start state to the end state. A fractional 
	  value (e.g., 2.75) means the animation will be halted midway through its final cycle. A 
	  value of 0 means that there will be no animation; negative values are converted to 0. As 
	  its name implies, infinite means the animation will never end. Use with caution.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
body {animation-iteration-count: 2, 1, 7.5875;}
ol.dance {animation-iteration-count: infinite;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!-- <h3><b>animation-name</b>  <b>Inh. N Anim. N</b></h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>animation-name</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>&lbrack; <i>&lt;single-animation-name&gt;</i> &vert; none &rbrack;#</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>none</td>
    </tr>
	<tr>
	  <td><b>Computed As value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements, ::before and ::after pseudoelements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the declared name(s) of CSS animation(s). Each name refers to a CSS animation 
	  keyframe atrule. If no animation name is declared or the keyword none is supplied, the 
	  animation is not run regardless of the values of any other animation properties. For 
	  example, given animation-name: bounce, none, jumper and that the animation name jumper 
	  has not been defined, the first animation will run but the second and third will not.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
html {animation-name: turn, slide, none;}
h2 {animation-name: flip;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!-- <h3><b>animation-play-state</b>  <b>Inh. N Anim. N</b></h3> -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>animation-play-state</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>&lbrack; running &vert; paused &rbrack;#</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>running</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements, ::before and ::after pseudoelements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the run state of one or more CSS animations. The default state of running is the most useful in static CSS environments, but it can be used to easily stop or start animations via DOM scripting or interactive CSS (e.g., :hover).</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
pre {animation-play-state: 
running, paused, running;} table {animation-play-state: running;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3><b>animation-timing-function</b>  <b>Inh. N Anim. N</b></h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>animation-timing-function</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>&lbrack; ease &vert; linear &vert; ease-in &vert; ease-out &vert; ease-in-out &vert; step-start &vert; step-end &vert; steps(<i>&lt;integer&gt;</i>, start) &vert; steps(<i>&lt;integer&gt;</i>, end) &vert; cubic-bezier(<i>&lt;number&gt;</i>, <i>&lt;number&gt;</i>,<i>&lt;number&gt;</i>,<i>&lt;number&gt;</i>) &rbrack;#</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>ease</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements, ::before and ::after pseudo elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines how an animation is run over the course of the animation's full cycle or within 
	  an individual keyframe, depending on where the property is used. The keywords are all defined 
	  to have cubicbezier() equivalents; for example, linear is equivalent to cubic-bezier(0,0,1,1). 
	  They should therefore have consistent effects across user agents ---but, as always, authors 
	  are cautioned not to count on that.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
h1 {animation-timing-function: ease, ease-in,
cubic-bezier(0.13,0.42,0.67,0.75)} p {animation-timing-function:
linear;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3><b>backface-visibility</b>  <b>Inh. N Anim. N</b></h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>backface-visibility</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>visible &vert; hidden</td>
	</tr>
    <tr>
	  <td><b>Initial value</b></td>
	  <td>visible</td>
	</tr>
    <tr>
	  <td><b>Computed value</b></td>
	  <td>As declared </td>
	</tr>
    <tr>
	  <td><b>Applies to</b></td>
	  <td>Any transformable element</td>
	</tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines whether the back side of an element is visible once the element has been 
	  rotated in a simulated 3D space and is "facing away" from the viewer. If the value is 
	  hidden, the element will be effectively invisible until it is rotated such that the 
	  front side of the element is once more "facing toward" the viewer.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
div.card {backface-visibility: hidden;}  
span.cubeside {backface-visibility: visible;}    
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3><b>background</b>   <b>Inh. N Anim. P</b></h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>background</h3></th>
	  <th align="right"><h3>Inh. N Anim. P</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Animatable</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
<b>Values</b> &lbrack; <i>&lt;bg-layer&gt;</i> , &rbrack;&ast; <i>&lt;final-bg-layer&gt;</i>    
<b>Initial value</b>  Refer to individual properties   
<b>Computed value</b> Refer to individual properties 
<b>Applies to</b>     All elements     
<b>Animatable</b>     Refer to individual background properties to see 
    which are animatable     
<p><b>Description</b>    A shorthand way of expressing the various 
    background properties of one or more element     
    backgrounds using a single declaration. As with  
    all shorthands, this property will set all of    
    the allowed values (e.g., the repeat, position,  
    and so on) to their defaults if the values are   
    not explicitly supplied. 

Thus, the following two rules will have the same appearance:
background: yellow;
background: yellow none top left repeat; Furthermore, these defaults
can override previous declarations made with more specific background
properties. For example, given the following rules:

h1 {background-repeat: repeat-x;} h1, h2 {background: yellow
url(headback.gif);} the repeat value for both h1 and h2 elements will
be set to the default of repeat, overriding the previously declared
value of repeat-x.

When declaring multiple backgrounds, only the last may have a
background color. In cases where multiple background images overlap,
the images are stacked with the first highest and the last lowest.
This is the exact reverse of how overlapping is handled in CSS
positioning, and so may seem counterintuitive.

<p><b>Examples</b></p>
<pre>
body {background: white url(bg41.gif) fixed center
repeat-x;} p {background:
url(/pix/water.png) center repeat-x, top left url(/pix/stone.png)
#555;} pre {background: yellow;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3><b>background-attachment</b>  <b>Inh. N Anim. N</b></h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>background-attachments</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Animatable</b></td>
	  <td></td>
    </tr>	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
<b>Values</b>   &lbrack; scroll &vert; fixed &vert; local &rbrack;#  
<b>Initial value</b>   scroll  
<b>Computed value</b>  As declared  
<b>Applies to</b>   All elements 
<p><b>Description</b>  Defines whether background images scroll along with
    the element when the document is scrolled. This 
property can be used to create "aligned" 
backgrounds; for more details, see Chapter 9 of 
<i>CSS: The Definitive Guide</i>, 4th Edition. 

<p><b>Examples</b></p>
<pre>
body {background-attachment: scroll, scroll, fixed;}
div.fixbg {background-attachment: fixed;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3><b>background-blend-mode</b>  <b>Inh. N Anim. N</b></h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>background-blend-mode</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Animatable</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
<b>Values</b>   &lbrack; normal &vert; multiply &vert; screen &vert; overlay &vert; darken
    &vert; lighten &vert; color-dodge &vert; color-burn &vert; hard-light
    &vert; soft-light &vert; difference &vert; exclusion &vert; hue &vert;
    saturation &vert; color &vert; luminosity &rbrack;# 
<b>Initial value</b>  normal 
<b>Computed value</b>  As declared 
<b>Applies to</b>    All elements 
<p><b>Description</b>   Changes how overlapping background images are
composited against an "empty" backdrop. The "backdrop" here is a
transparent layer underneath the background color. The default of
normal imposes simple alpha blending, as CSS has permitted since its
inception. The others cause the background image and its backdrop to
be combined in various ways; for example, lighten means that the final
result will show, at each pixel, either the image or its backdrop,
whichever is lighter. darken is the same, except the darker of the two
pixels will be shown. The results of these are likely to be familiar
to users of Photoshop or any other graphic-editing tool. Compositing
of multiple background layers is done back to front. 
<p><b>Examples</b></p>
<pre>
li.shadowed {background-blend-mode: darken;} aside
{background-blend-mode: color-burn, luminosity, darken;} 
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>background-clip Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>background-clip</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Animatable</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
<b>Values</b> &lbrack; border-box &vert; padding-box &vert; content-box &vert; text &rbrack;#
<b>Initial value</b> border-box <b>Computed value</b> As declared

<b>Applies to</b> All elements

<p><b>Description</b> Defines the boundary within the element box at which the
background is clipped (that is, no longer drawn). Historically, this has
been equivalent to the default value of border-box, where the background
goes to the outer edge of the border area. This property allows more
constrained clipping boxes at the outer edge of the padding area and at
the content edge itself.

<p><b>Examples</b></p>
<pre>
body {background-clip: content-box;}
.callout {background-clip: content-box, border-box, padding-box;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>background-color  Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>background-color</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Animatable</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values    <i>&lt;color&gt;</i> 
Initial value  transparent 
Computed value   As declared  
Applies to    All elements
Description  Defines a solid color for the 
    background of the element. This 
color fills the box defined by the  
value of background-clip---by  
default, the content, padding, and  
 border areas of the element,
extending to the outer edge of the  
element's border. Borders that have 
transparent sections (such as  
dashed borders) will show the  
background color through the
transparent sections in cases where 
the background color extends into 
the border area. 
<p><b>Examples</b></p>
<pre>
h4 {background-color: white;}
p {background-color: 
rgba(50%,50%,50%,0.33);} 
pre {background-color: #FF9;} 
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3><b>background-image</b>  <b>Inh. N Anim. N</b></h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>background-image</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Animatable</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
<b>Values</b>  &lbrack; <i>&lt;image&gt;</i> &vert; none &rbrack;# 
<b>Initial value</b>  none 
<b>Computed value</b>  As declared, but with all URIs made absolute 
<b>Applies to</b>  All elements 
<p><b>Description</b>  Places one or more images in the background of the
element. Depending on the value of backgroundrepeat, the image may tile
infinitely, along one axis, or not at all. The initial background image
(the origin image) is placed according to the value of
background-position. 
<p><b>Examples</b></p>
<pre>
 body {background-image:
 url(bg41.gif), url(bg43.png), url(bg51.jpg);} h2 {background-image:
 url(http://www.pix.org/dots.png);}  
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3><b>background-origin</b>  <b>Inh. N Anim. N</b></h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>background-origin</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>&lbrack; border-box &vert; padding-box &vert; content-box &rbrack;# </td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>padding-box</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the boundary within the element box against which background image positioning is 
	  calculated. Historically, this has been equivalent to the default value of padding-box. This 
	  property allows for different positioning contexts. Note that if the value of background-origin 
	  is "further out" than the value for background-clip, and the image is positioned to an edge, 
	  part of it may be clipped. For example: div#example {background-origin: border-box; background-clip: 
	  content-box; background-position: 100% 100%;} In this case the image will be placed so that its 
	  bottom-right corner aligns with the bottom-right   corner of the outer border edge, but the only 
	  parts of it that will be visible are those that fall within the content area.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
html, body {background-origin: border-box;} 
h1 {background-origin: content-box, padding-box;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>background-position  Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>background-position</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Value</b></td>
	  <td><i>&lt;position&gt;</i>&#35;</td>
	</tr>
    <tr>
	  <td><b>Initial value</b></td>
	  <td>0% 0%</td>
	</tr>
    <tr>
	  <td><b>Computed value</b></td>
	  <td>The absolute length offsets, if <i>&lt;length&gt;</i> is specified; otherwise, percentage values</td>
	</tr>
    <tr>
	  <td><b>Percentages</b></td>
	  <td>Refer to the corresponding point on both the element and the origin image</td>
	</tr>
    <tr>
	  <td><b>Applies to</b></td>
	  <td>Block-level and replaced elements</td>
	</tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the position(s) of one or more backgrounds' origin images (as defined by background-image); 
	  this is the point from which any background repetition or tiling will occur. Percentage values define 
	  not only a point within the element, but also the same point in the origin image itself. That means 
	  (for example) an image can be centered by declaring its position to be 50% 50%. When percentage or 
	  length values are used, the first is always the horizontal position and the second is the vertical 
	  position. If only one value is given, it sets the horizontal position, while the missing value is 
	  assumed to be either center or 50%. Negative values are permitted and may place the origin image 
	  outside the element's content area without actually rendering it. The context within which an origin 
	  image is placed can be affected by the value of background-origin.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
body {background-position: top 
center;} div#navbar
{background-position:
right, 50% 75%, 0 40px;} pre
{background-position: 10px 50%;} 
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3><b>background-repeat</b>  <b>Inh. N Anim. N</b></h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>background-repeat</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Value</b></td>
	  <td><i>&lt;repeat-style&gt;</i>&#35;</td>
	</tr>
	<tr>
	  <td><b>Definition</b></td>
	  <td><i>&lt;repeat-style&gt;</i> repeat-x &vert; repeat-y &vert; &lbrack; repeat &vert; space &vert; round &vert; no-repeat &rbrack;{1,2}.</td>
    </tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>repeat</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the tiling pattern for one or more background images. The repetition begins from the origin image, which is defined as the value of background-image and is placed according to the value of background-position (and possibly background-origin). For the keywords space and round, the image is tiled as many times as it will fit in the background area without being clipped, and then the first and last images are placed against their respective background edges. The difference is that space causes the intervening images to be regularly spaced, and round causes them to be stretched to touch each other. Note that repeat-x is equivalent to repeat no-repeat, and repeat-y is equivalent to no-repeat repeat.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
body {background-repeat: no-repeat;}
h2 {background-repeat: repeat-x, repeat-y;} ul {background-repeat:
repeat-y, round space, repeat;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3><b>background-size</b>  <b>Inh. N Anim. Y</b></h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>background-size</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values   &lbrack; &lbrack; *&lt;length&gt;* &vert; *&lt;percentage&gt;* &vert; auto  
&rbrack;{1,2} &vert; cover &vert; contain &rbrack;# 
Initial value   auto 
Computed value  As declared, but with all lengths made absolute and  
  any missing auto keywords added 
Applies to   All elements 
Description  Defines the size of one or more background origin
    images. If two keywords are used (e.g., 50px 25%),   
the first defines the horizontal size of the image   
and the second defines the vertical size. The origin 
image can be deformed to exactly cover the   
background with 100% 100%. By contrast, cover scales 
up the image to cover the entire background even if some of it exceeds
the background area and is thus clipped, and contain scales up the
origin image so that at least one of its dimensions exactly fills the
corresponding axis of the background area. 

<p><b>Examples</b></p>
<pre>
body {background-size: 100% 90%;}
div.photo {background-size: cover;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border    Inh. N Anim. P</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border</h3></th>
	  <th align="right"><h3>Inh. N Anim. P</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values    &lbrack; *&lt;border-width&gt;* ‖ *&lt;border-style&gt;* ‖
 *&lt;bordercolor&gt;* &rbrack;
Initial value    Refer to individual properties 
Computed value   As declared 
Applies to    All elements    
  Border width and color; not border style    
Animatable 
Description  A shorthand property that defines the width, color,
    and style of an element's border. Note that while 
 none of the values are actually required, omitting  
 a border style will result in no border being  
 applied because the default border style is none.   

<p><b>Examples</b></p>
<pre>
h1 {border: 2px dashed olive;} a:link {border: blue 
solid 1px;} 
     
p.warning {border: double 5px red;} 
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border-bottom Inh. N Anim. P</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-bottom</h3></th>
	  <th align="right"><h3>Inh. N Anim. P</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values&lbrack; *&lt;border-width&gt;* ‖ *&lt;border-style&gt;* ‖
    *&lt;bordercolor&gt;* &rbrack;
Initial value See individual properties
ComputedSee individual properties (border-width, etc.)
  value   
Applies to    All elements

Animatable    Border width and color; not border style

Description   A shorthand property that defines the width, color,
    and style of the bottom border of an element. As

with border, omission of a border style will result in no border
appearing.

<p><b>Examples</b></p>
<pre>
ul {border-bottom: 0.5in groove green;}
a:active {border-bottom: purple 2px dashed;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border-bottom-color Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-bottom-color</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-bottom-color</h3></th>
	  <th><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td><i>&lt;color&gt;</i></td>
	</tr>
    <tr>
	  <td><b>Initial value</b></td>
	  <td>currentColor</td>
	</tr>
    <tr>
	  <td><b>Computed value</b></td>
	  <td>A Color</td>
	</tr>
    <tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
	</tr>
    <tr>
	  <td><b>Description</b></td>
	  <td>Defines the color for the visible portions of the bottom border of an element. The 
	  border's style must be something other than none or hidden for any visible border to 
	  appear.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
ul {border-bottom-color: green;}
a:active {border-bottom-color: purple;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border-bottom-left-radius Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-bottom-left-radius</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values&lbrack; *&lt;length&gt;* &vert; *&lt;percentage&gt;* &rbrack;{1,2}
Initial value 0
ComputedTwo values, each a *&lt;percentage&gt;* or *&lt;length&gt;*
  value   made absolute
Percentages   Calculated with respect to the relevant dimension of
    the border box
Applies to    All elements, except internal table elements
Description   Defines the rounding radius for the bottom-left corner
    of an element's border. If two values are supplied,
    the first is the horizontal radius and the second is
    the vertical radius. See border-radius for a
    description of how the values create the rounding
    shape.

<p><b>Examples</b></p>
<pre>
h1 {border-bottom-left-radius: 10%;}
h2 {border-bottom-left-radius: 1em 10px;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border-bottom-right-radius Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-bottom-right-radius</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values&lbrack; *&lt;length&gt;* &vert; *&lt;percentage&gt;* &rbrack;{1,2}
Initial value 0
ComputedTwo values, each a *&lt;percentage&gt;* or *&lt;length&gt;*
  value   made absolute
Percentages   Calculated with respect to the relevant dimension of
    the border box
Applies to    All elements, except internal table elements
Description   Defines the rounding radius for the bottom-right
    corner of an element's border. If two values are
    supplied, the first is the horizontal radius and the
    second is the vertical radius. See border-radius for a description of how
	the values create the rounding shape.

<p><b>Examples</b></p>
<pre>
h1 {border-bottom-right-radius: 10%;}
h2 {border-bottom-right-radius: 1em 10px;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border-bottom-style Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-bottom-style</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Valuesnone &vert; hidden &vert; dotted &vert; dashed &vert; solid &vert; double
    &vert; groove &vert; ridge &vert; inset &vert; outset
Initial value none
ComputedAs declared
  value   
Applies to    All elements
Description   Defines the style for the bottom border of an ele‐
ment. The value must be something other than none or hidden for any
border to appear.
<p><b>Examples</b></p>
<pre>
ul {border-bottom-style: groove;}
a:active {border-bottom-style: dashed;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border-bottom-width Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-bottom-width</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>&lbrack; thin &vert; medium &vert; thick &vert; *&lt;length&gt;* &rbrack;</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>See individual properties</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>See individual properties (border-top-style, etc.)</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the width for the bottom border of an element, which will take effect only if 
	  the border's style is something other than none or hidden. If the border style is none, 
	  the border width is effectively reset to 0. Negative length values are not permitted.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
ul {border-bottom-width: 0.5in;}
a:active {border-bottom-width: 2px;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border-collapse Inh. Y Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-collapse</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Valuescollapse &vert; separate &vert; inherit
Initial value separate
ComputedAs declared value   
Applies to    Elements with the display value table or tableinline
Description   Defines the layout model used in laying out the
    borders in a table---i.e., those applied to cells,
    rows, and so forth. Although the property applies only
    to tables, it is inherited by all the elements within
    the table and actually used by them.

<p><b>Example</b></p>
<pre>
table {border-collapse: separate; border-spacing: 3px 5px;}
</pre>

Note  In CSS2, the default was collapse.
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border-color  Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-color</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>*&lt;color&gt;*{1,4}</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>See individual properties</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>A shorthand property that sets the color for the visible portions of the overall border 
	  of an element or sets a different color for each of the four sides. Remember that a border's 
	  style must be something other than none or hidden for any visible border to appear.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
h1 {border-color: purple;}
a:visited {border-color: maroon;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!-- <h3>border-image  Inh. N Anim. P</h3>  -->
<!-- <h3><div id="left">border-image</div><div align="right">Inh. N Anim. P</div></h3> -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--
#left {
    float: left;
    text-align: left;
    padding-right: 10px;
}

#center {
    text-align: center;
}

#right {
    float: right;
    text-align: right;
    padding-left: 10px;
}
-->
<table>
  <thead>
    <tr>
	  <th><h3>border-image</h3></th>
	  <th>Inh. N Anim. P</th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>&lt;border-image-source&gt; ‖  &lt;border-image-slice&gt; &lbrack; /<br>
	  &lt;border-image-width&gt; | / &lt;border-image-width&gt;? /<br>
	  &lt;border-image-outset&gt; &rbrack;? ‖ &lt;border-image-repeat&gt;</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>See individual properties</td>
	</tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>See individual properties</td>
	</tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>See individual properties</td>
	</tr>
	<tr>
	  <td><b>Animatable</b></td>
	  <td>Refer to individual border-image properties to see which are animatable.</td>
	</tr>
	  <td><b>Description    </b></td>
	  <td>A shorthand property that defines the source, slicing pattern, border width, degree of extension,  
   and repetition of an image-based border. The syntax is somewhat unusual compared to the rest of CSS, so 
   take extra time with it. For example, three of the five values possible are slash-separated and must be 
   listed in a specific order.<br><br>Note that it is effectively impossible to take a 
   simple image (say, a star) and repeat it around the edges of an element. To create that effect, you must 
   create a single image that contains nine copies of the image you wish to repeat in a 3×3 grid. It may   
   also be necessary to set border-width (<i>not</i> border-imagewidth) to be large enough to show the    
   image, depending on the value of border-image-outset.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>div.starry {border-image;
  url(stargrid.png) 5px repeat;}
aside {border-image: url(asides.png)
  100 50 150 / 8 3 13 / 2 stretch round;}</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border-image-outset Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-image-outset</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>&lbrack; *&lt;length&gt;* &vert; *&lt;number&gt;* &rbrack;{1,4}</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>0</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>Four values, each a number or *&lt;length&gt;* made absolute</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements, except internal table elements when
    border-collapse is collapse</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the distance by which a border image may exceed the border area of the element. 
	  The values define distances from the top, right, bottom, and left edges of the border image, 
	  in that order. Numbers are calculated with respect to the image's intrinsic coordinate system; 
	  thus, for a raster image, the number 7 is taken to mean seven pixels. Images in formats such 
	  as SVG may have different coordinate systems. Negative values are not permitted.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
aside {border-image-outset: 2;}
div#pow {border-image-outset: 10 17 13 5;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border-image-repeat Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-image-repeat</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>&lbrack; stretch &vert; repeat &vert; round &vert; space &rbrack;{1,2}</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>stretch</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>Two keywords, one for each axis </td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements, except internal table elements when border-collapse is collapse</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>the sides of a border image. stretch causes a single copy of the image to be stretched to 
	  fit the border segment (top, right, bottom, or left). repeat "tiles" the image in a manner 
	  familiar from background images, though border images are only ever tiled along one axis. 
	  round "tiles" the border image as many times as it will fit without clipping, then (if necessary) 
	  scales the entire set of tiled images to exactly fit the border segment.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
div.starry {border-image-repeat: repeat;}
aside {border-image-repeat: stretch round;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border-image-slice Inh. N Anim. P</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-image-slice</h3></th>
	  <th align="right"><h3>Inh. N Anim. P</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>&lbrack; *&lt;number&gt;* &vert; *&lt;percentage&gt;* &rbrack;{1,4} && fill?</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>100% </td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>Four values, each a number or percentage, and optionally the fill keyword</td>
    </tr>
	<tr>
	  <td><b>Percentage</b></td>
	  <td>Refer to the size of the border image</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements, except internal table elements when border-collapse is collapse 
	  <i>&lt;number&gt;</i> and <i>&lt;percentage&gt;</i> values only.</td>
    </tr>
	<tr>
	  <td><b>Animatable</b></td>
	  <td><i>&lt;number&gt;</i> and <i>&lt;percentage&gt;</i> values only</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines "slice distances," which are offsets from the top, right, bottom, and left edges 
	  of the border image. Taken together, they divide the image into nine regions, which correspond 
	  to the eight segments of the element's border (four corners and four sides) and the element's 
	  background area. In cases where two opposite regions combine to exceed the total of the dimension 
	  they share, both are made completely transparent. For example, if the top slice offset value is 10 
	  and the bottom slice offset value is 20, but the source image is only 25 pixels tall, the two exceed 
	  the height of the image. Thus, both the top and bottom segments of the border will be entirely 
	  transparent. The same holds for right and left slices and width. Corners are never forcibly made 
	  transparent, even in cases where their slices may overlap in the source image.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
div.starry {border-image-slice: 5px;}
aside {border-image-slice: 100 50 150;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border-image-source Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-image-source</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>none &vert; <i>&lt;image&gt;</i></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>none</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>none, or the image with its URI made absolute</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements, except internal table elements when border-collapse is collapse</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Supplies the location of the image to be used as an element's border image.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
div.starry {border-image-source:
url(stargrid.png);}
aside {border-image-source: url(asides.png);}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border-image-width Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-image-width</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>&lbrack; <i>&lt;length&gt;</i> &vert; <i>&lt;percentage&gt;</i> &vert; <i>&lt;number&gt;</i> 
	  &vert; auto &rbrack;{1,4}</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>1</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>Four values, each a percentage, a number, a <i>&lt;length&gt;</i> made absolute, or the 
	  auto keyword Relative to the width/height of the entire border</td>
    </tr>
	<tr>
	  <td><b>Percentages</b></td>
	  <td>image area; that is, the outer edges of the border box</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements, except table elements when bordercollapse is collapse</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines an image width for each of the four sides of an image border. Border image slices 
	  that have a different width than the border image width value are scaled to match it, which 
	  may impact how they are repeated. For example, if the right edge of an image border is 10 pixels 
	  wide, but border-image-width: 3px has been declared, the border images along the right side are 
	  scaled to be three pixels wide. Note that border-image-width is different from border-width: a 
	  border image's width can be different than the width of the border area. In cases where the image 
	  is wider or taller than the border area, it will be clipped by default (but border-imageoutset may 
	  prevent this). If it is narrower or shorter than the border area, it will not be scaled up. Negative 
	  values are not permitted.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
aside {border-image-width: 8 3 13;}
div#pow{border-image-width: 25px 35;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border-left  Inh. N Anim. P</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-left</h3></th>
	  <th align="right"><h3>Inh. N Anim. P</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>&lbrack; *&lt;border-width&gt;* ‖ *&lt;border-style&gt;* ‖ *&lt;bordercolor&gt;* &rbrack;</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>See individual properties</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>See individual properties (border-width, etc.)</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Animatable</b></td>
	  <td>Border width and color; not border style</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>A shorthand property that defines the width, color, and style of the left border 
	  of an element. As with border, omission of a border style will result in no border appearing.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
p {border-left: 3em solid gray;} pre {border-left:  
double black 4px;}  
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border-left-color Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-left-color/h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>*&lt;color&gt;*</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>currentColor</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>A color</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the color for the visible portions of the left border of an element. The border's 
	  style must be something other than none or hidden for any visible border to appear.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
p {border-left-color:  gray;} 
pre {border-left-color:  black;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border-left-style Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-left-style</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>none &vert; hidden &vert; dotted &vert; dashed &vert; solid &vert; double &vert; groove &vert; ridge &vert; inset &vert; outset</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>none</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>declared value</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the style for the left border of an element. The value must be something other 
	  than none or hidden for any border to appear.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
p {border-left-style: solid;}
pre {border-left-style: double;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border-left-width Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-left-width</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>thin &vert; medium &vert; thick &vert; *&lt;length&gt;*</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>medium</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>absolute length, or 0 if the style of the border is none or hidden; otherwise, as declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the width for the left border of an element, which will take effect only if the 
	  border's style is something other than none or hidden. If the border style is none, the border 
	  width is effectively reset to 0. Negative length values are not permitted.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
p {border-left-width: 3em;}
pre {border-left-width: 4px;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border-radius Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-radius</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>&lbrack; *&lt;length&gt;* &vert; *&lt;percentage&gt;* &rbrack;{1,4} &lbrack; / &lbrack; *&lt;length&gt;* &vert; *&lt;percentage&gt;* &rbrack;{1,4} &rbrack;?</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>0</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>Four values, each a <i>&lt;percentage&gt;</i> or <i>&lt;length&gt;</i> 
   made absolute</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements, except internal table elements </td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>A shorthand property that defines the rounding radius for the bottom-right corner of an 
	  element's border. The actual corners will be the height and width declared. Thus, given: 
	  .callout {border-radius: 10px;} each corner of an element with a class of callout will 
	  have a rounding that is 10 pixels across, as measured from the beginning of the rounding 
	  to the outer side edge of the element, and is similarly 10 pixels high. This can be visualized 
	  as if the element had 10-pixel-radius (20-pixel-diameter) circles drawn in its corners, and then 
	  the border were bent along the circles' edges. Using fewer than four values causes the supplied 
	  values to be repeated in the familiar pattern (see margin, padding, etc.), but with a slight offset. 
	  Rather than being Top-Right-Bottom-Left (TRBL, or "trouble"), the pattern is 
	  TopLeft-TopRightBottomRight-BottomLeft (TLTRBRBL, or "tilter burble"). Otherwise, the repeat 
	  pattern is the same. Percentages, when used, are calculated with respect to the size of the 
	  element's border box (the box defined by the outer edges of the element's border area) dimension 
	  on the related axis.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
a&lbrack;href&rbrack; {border-radius: 0.5em 50%;}
.callout {border-radius:
10px 20px 30px 40px /
1em 2em 3em 4em;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border-right Inh. N Anim. P</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-right</h3></th>
	  <th align="right"><h3>Inh. N Anim. P</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>&lbrack; <i>&lt;border-width&gt;</i> ‖ <i>&lt;border-style&gt;</i> ‖ <i>&lt;bordercolor&gt;</i> &rbrack;</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>See individual properties</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>See individual properties (border-width, etc.)</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>A shorthand property that defines the width, color, and style of the right border of an 
	  element. As with border, omission of a border style will result in no border appearing.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
img {border-right: 30px dotted blue;}
h3 {border-right: cyan 1em inset;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border-right-color Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-right-color</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td><i>&lt;color&gt;</i></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>currentColor</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>color</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the color for the visible portions of the right border of an element. The 
	  border's style must be something other than none or hidden for any visible border to appear.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
img {border-right-color: blue;}
h3 {border-right-color: cyan;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border-right-style Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-right-style</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>none &vert; hidden &vert; dotted &vert; dashed &vert; solid &vert; double &vert; groove &vert; ridge &vert; inset &vert; outset</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>none </td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the style for the right border of an element. The value must be something other 
	  than none or hidden for any border to appear.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
img {border-right-style: dotted;}
h3 {border-right-style: inset;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border-right-width Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-right-width</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>thin &vert; medium &vert; thick &vert; <i>&lt;length&gt;</i></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>medium</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>absolute length, or 0 if the style of the border is none or hidden; otherwise, as declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the width for the right border of an element, which will take effect only if the 
	  border's style is something other than none or hidden. If the border style is none, the border 
	  width is effectively reset to 0. Negative length values are not permitted.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
img {border-right-width: 30px;}
h3 {border-right-width: 1em;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border-spacing Inh. Y Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-spacing</h3></th>
	  <th align="right"><h3>Inh. Y Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td><i>&lt;length&gt;</i> <i>&lt;length&gt;</i>? </td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>0</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>Two absolute lengths</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>Elements with the display value table or tableinline </td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the distance between table cell borders in the separated borders table layout 
	  model. The first of the two length values is the horizontal separation and the second is 
	  the vertical separation. Although the property applies only to tables, it is inherited by 
	  all of the elements within the table.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
table {border-spacing: 0;}
table {border-spacing: 3px 5px;}
</pre>
      </td>
	</tr>
	<tr>
	  <td><b>Note</b></td>
	  <td>This property is ignored unless the value of bordercollapse is separate.</td>
    </tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border-style Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-style</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>&lbrack; none &vert; hidden &vert; solid &vert; dotted &vert; dashed &vert;   
 double &vert; groove &vert; ridge &vert; inset &vert; outset
 &rbrack;{1,4}  </td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>See individual properties   </td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>See individual properties (border-top-style, etc.)  </td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>A shorthand property used to define the styles for the overall border of an element or 
	  for each side individually. The value of any border must be something other than none or 
	  hidden for the border to appear. Note that setting border-style to none (its default value) 
	  will result in no border at all. In such a case, any value of border-width will be ignored 
	  and the width of the border will be set to 0. Any unrecognized value from the list of values 
	  should be reinterpreted as solid.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
h1 {border-style: solid;} 
img {border-style:inset;}     
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  border-top  Inh. N Anim. P</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-top</h3></th>
	  <th align="right"><h3>Inh. N Anim. P</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>&lbrack; <i>&lt;border-width&gt;</i> ‖ <i>&lt;border-style&gt;</i> ‖ <i>&lt;bordercolor&gt;</i> &rbrack;</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>See individual properties</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>See individual properties (border-width, etc.)</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Animatable</b></td>
	  <td>Border width and color; not border style</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>A shorthand property that defines the width, color, and style of the top border of 
	  an element. As with border, omission of a border style will result in no border appearing.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
ul {border-top: 0.5in solid black;}
h1 {border-top: dashed 1px gray;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<p><b>Examples</b></p>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border-top-color Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-top-color</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td><i>&lt;color&gt;</i></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>currentColor Computed value A color</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Sets the color for the visible portions of the top border of an element. The border's style must be something other than none or hidden for any visible border to appear.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
ul {border-top-color: black;}
h1 {border-top-color: gray;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border-top-left-radius Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-too-left-radius</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>&lbrack; <i>&lt;length&gt;</i> &vert; <i>&lt;percentage&gt;</i> &rbrack;{1,2}</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>0</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>Two values, each a <i>&lt;percentage&gt;</i> or <i>&lt;length&gt;</i> made absolute</td>
    </tr>
	<tr>
	  <td><b>Percentages</b></td>
	  <td>Calculated with respect to the relevant dimension of the border box</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements, except internal table elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the rounding radius for the top-left corner of an element's border. If two 
	  values are supplied, the first is the horizontal radius and the second is the vertical 
	  radius. See border-radius for a description of how the values create the rounding shape.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
h1 {border-top-left-radius: 10%;}
h2 {border-top-left-radius: 1em 10px;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border-top-right-radius Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-top-right-radius</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>&lbrack; <i>&lt;length&gt;</i> &vert; <i>&lt;percentage&gt;</i> &rbrack;{1,2}</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>0</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>Two values, each a <i>&lt;percentage&gt;</i> or <i>&lt;length&gt;</i> made absolute</td>
    </tr>
	<tr>
	  <td><b>Percentage</b></td>
	  <td>Calculated with respect to the relevant dimension of the border box.</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements, except internal table elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the rounding radius for the top-right corner of an element's border. If two values are supplied, the first is the horizontal radius and the second is the vertical radius. See border-radius for a description of how the values create the rounding shape.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
h1 {border-top-right-radius: 10%;}
h2 {border-top-right-radius: 1em 10px;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border-top-style Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-top-style</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>none &vert; hidden &vert; dotted &vert; dashed &vert; solid &vert; double &vert; groove 
	  &vert; ridge &vert; inset &vert; outset</td>
	</tr>
	  <td><b>Initial value</b></td>
	  <td>none</td>
    </tr>
	</tr>
	  <td><b>Computed As value</b></td>
	  <td>declared</td>
    </tr>
	</tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	</tr>
	  <td><b>Description</b></td>
	  <td>Defines the style for the top border of an element. The value must be something other than none or hidden for any border to appear.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
ul {border-top-style: solid;}
h1 {border-top-style: dashed;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border-top-width Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-top-width</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>thin &vert; medium &vert; thick &vert; <i>&lt;length&gt;</i></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>medium</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>An absolute length, or 0 if the style of the border is
  none or hidden; otherwise, as declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the width for the top border of an element, which will take effect only if the 
	  border's style is something other than none or hidden. If the style is none, the width is 
	  effectively reset to 0. Negative length values are not permitted.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
ul {border-top-width: 0.5in;}
h1 {border-top-width: 1px;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>border-width Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>border-width</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>&lbrack; thin &vert; medium &vert; thick &vert; <i>&lt;length&gt;</i> &rbrack;{1,4} </td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>See individual properties</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>See individual properties (border-top-style, etc.)</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>A shorthand property that defines the width for the overall border of an element or 
	  for each side individually. The width will take effect for a given border only if the 
	  border's style is something other than none or hidden. If the border style is none, the 
	  border width is effectively reset to 0. Negative length values are not permitted.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
h1 {border-width: 2ex;}
img {border-width: 5px thick thin 1em;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>bottom    Inh. N Anim. P</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>bottom</h3></th>
	  <th align="right"><h3>Inh. N Anim. P</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td><i>&lt;length&gt;</i> &vert; <i>&lt;percentage&gt;</i> &vert; auto</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>auto</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>For static elements, auto; for length values, the corresponding absolute length; 
	  for percentage values, the specified value; otherwise, auto</td>
    </tr>
	<tr>
	  <td><b>Percentage</b></td>
	  <td>Refer to the height of the containing block.</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>Positioned elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the offset between the bottom outer margin edge of a positioned element and 
	  the bottom edge of its containing block. For relatively positioned elements, if both 
	  bottom and top are auto, their computed values are both 0; if one of them is auto, it 
	  becomes the negative of the other; if neither is auto, bottom will become the negative 
	  of the value of top.</td>
    </tr>
	<tr>
	  <td><b>Animatable</b></td>
	  <td><i>&lt;length&gt;</i> and <i>&lt;percentage&gt;</i> values only</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
div#footer {position: fixed; bottom: 0;}
sup {position: relative; bottom: 0.5em; vertical-align: baseline;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>box-decoration-break Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>box-decoration-break</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>slice &vert; clone</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>slice</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines whether the decorations---the background, padding, borders, rounded corners, 
	  border image, and box shadow---of a box that has been rendered in multiple pieces are 
	  applied to each piece separately or applied to the entire box before it is broken apart. 
	  The most common case is an inline element that wraps across one or more line breaks. With 
	  the default behavior, slice, the pieces of the inline element are drawn as though the 
	  whole element was laid out in a single line and then sliced apart at each line break. If 
	  clone is declared, then each piece of the element is decorated as though they were separate 
	  elements sharing the same styles. box-decoration-break also applies to block boxes that 
	  are split across columns or pages.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
span {box-decoration-break: clone;} a
{box-decoration-break: slice;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>box-shadow Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>box-shadow</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>none &vert; &lbrack;inset? && <i>&lt;length&gt;</i>{2,4} && <i>&lt;color&gt;</i>?&rbrack;#</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>none</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td><i>&lt;length&gt;</i> values as absolute length values; <i>&lt;color&gt;</i> values as 
	  computed internally; otherwise, as declared.</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines one or more shadows that are derived from the shape of the element box. 
	  Either outset ("drop") shadows or inset shadows can be defined, the latter with use 
	  of the optional inset keyword. Without that keyword, the shadow will be outset. The 
	  four length values that can be declared are, in order: horizontal offset, vertical 
	  offset, blur distance, and spread distance. When positive, the offset values go down 
	  and to the right; when negative, they go back and to the left. Positive spread values 
	  increase the size of the shadow and negative values contract it. Blur values cannot 
	  be negative. Note that all shadows are clipped by the element's border edge. Thus, an 
	  outset shadow is only drawn outside the border edge. A semitransparent or fully 
	  transparent element background will <i>not</i> reveal an outset shadow "behind" the element. 
	  Similarly, inset shadows are only visible inside the border edge and are never drawn 
	  beyond it.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
h1 {box-shadow: 5px 10px gray;} table th    
{box-shadow: inset 0.5em 0.75em 5px −2px    
rgba(255,0,0,0.5);} 
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>box-sizing  Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>box-sizing</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>content-box &vert; padding-box &vert; border-box</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>content-box</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements that accept width or height values</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines whether the height and width of the element define the dimensions of the 
	  content box (the historical behavior) or the border box. If the latter, the value of 
	  width defines the distance from the left outer border edge to the right outer border 
	  edge; similarly, height defines the distance from the top outer border edge to the 
	  bottom outer border edge. Any padding or border widths are "subtracted" from those 
	  dimensions instead of the historical "additive" behavior. Thus, given: body 
	  {box-sizing: border-box; width: 880px; padding: 0 20px;} the final width of the 
	  content area will be 840 pixels (880--20--20).</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
body {box-sizing: padding-box;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>caption-side Inh. Y Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>caption-side</h3></th>
	  <th align="right"><h3>Inh. Y Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>top &vert; bottom</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>top</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>Elements with the display value table-caption</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the placement of a table caption with respect to the table box. The caption 
	  is rendered as though it were a block-level element placed just before (or after) the 
	  table.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
caption {caption-side: top;}
</pre>
      </td>
	</tr>
	<tr>
	  <td><b>Note</b></td>
	  <td>The values left and right appeared in CSS2 but were later dropped due to a lack of 
	  widespread support.</td>
    </tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>clear     Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>clear</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>left &vert; right &vert; both &vert; none</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>none</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared </td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>Block-level elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines to which side (or sides) of an element no floating element may be placed. 
	  If normal layout of a cleared element would result in a floated element appearing on 
	  the cleared side, the cleared element is pushed down until it sits below (clears) the 
	  floated element. In CSS1 and CSS2, this is accomplished by automatically increasing 
	  the top margin of the cleared element. In CSS2.1, clearance space is added above the 
	  element's top margin, but the margin itself is not altered. In either case, the end 
	  result is that the element's top outer border edge is just below the bottom outer 
	  margin edge of a floated element on the declared side.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
h1 {clear: both;} p + h3 {clear: right;}    
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3> clip-path Inh. N Anim P</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>clip-path</h3></th>
	  <th align="right"><h3>Inh. N Anim. P</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>none &vert; <i>&lt;uri&gt;</i> &vert; &lbrack; &lbrack; inset() &vert; circle() &vert; ellipse() 
	  &vert; polygon() &rbrack; ‖ &lbrack; border-box &vert; padding-box &vert; 
	  content-box &vert; margin-box &vert; fill-box &vert; stroke-box &vert; 
	  view-box &rbrack; &rbrack;</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>none</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements (in SVG, applies to all graphics elements
   and all container elements except the defs element)</td>
    </tr>
	<tr>
	  <td><b>Animatable</b></td>
	  <td>inset(), circle(), ellipse(), and polygon() values</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines a clipping shape inside of which an element is visible, and outside of which 
	  it is invisible. url() values can be used to refer to an SVG file or an SVG clipPath 
	  element to be used as the clipping shape.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
p.clipped {clip-path: url(shapes.svg#cloud02);}
p.rounded {clip-path: ellipse(100px 50px at 75% 25%);}
p.diamond {clip-path:
polygon(50% 0, 100% 50%, 50% 100%, 0 50%);}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>clip-rule  Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>clip-rule</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>nonzero &vert; evenodd</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>nonzero </td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All SVG graphics elements (circle, ellipse, image, line, path, polygon, polyline, rect, 
	  text, and use) <i>if and only if</i> they are children of a clipPath element.</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Alters the way in which portions of a path that overlap each other cause the resulting 
	  shape to be filled. A nonzero rule causes the entire shape to be filled. evenodd can result 
	  in portions of the shape's interior being fully transparent.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
span.fullshape {clip-rule: nonzero;} span.knockouts 
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>color     Inh. Y Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>color</h3></th>
	  <th align="right"><h3>Inh. Y Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td><i>&lt;color&gt;</i></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>User agent--specific</td>
	</tr>
    <tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
	</tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
	</tr>
	  <td><b>Description</b></td>
	  <td>Defines the foreground color of an element, which <i>Description</i> in HTML 
	  rendering means the text of an element; raster images are not affected by color. 
	  This is also the color applied to any borders of the element, unless overridden by 
	  border-color or one of the other border color properties (border-top-color, etc.). 
	  For color keywords (such as navy) and RGB hex values (such as #008800 or #080), the 
	  computed value is the rgb() equivalent. For transparent, the computed value is 
	  rgba(0,0,0,0); for currentColor, the computed value is inherit. For all other values, 
	  the computed value is the same as the declared value.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
strong {color: rgb(255,128,128);} h3 {color: navy;}
p.warning {color: #ff0000;}
pre.pastoral {color: rgba(0%,100%,0%,0.33334);}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3><b>content</b>   <b>Inh. N Anim. N</b></h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>content</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>

<b>Values</b>    normal &vert; &lbrack; <i>&lt;string&gt;</i> &vert; <i>&lt;uri&gt;</i> &vert;   
<i>&lt;counter&gt;</i> &vert; attr(<i>&lt;identifier&gt;</i>) &vert;  
open-quote &vert; close-quote &vert; no-open-quote &vert;  
no-close-quote &rbrack;+  
<b>Initial value</b>    normal 
<b>Computed value</b>   For <i>&lt;uri&gt;</i> values, an absolute URI; for  
  attribute references, the resulting string; 
otherwise, as declared 
<b>Applies to</b>    ::before and ::after pseudo-elements

     Defines the generated content placed before or 
<b>Description</b>  after an element. By default, this is likely to be  
inline content, but the type of box the content     
creates can be defined using the property display.  
<p><b>Examples</b></p>
<pre>
p::before {content: &quot;Paragraph&hellip;&quot;;}     
a&lbrack;href&rbrack;::after {content: &quot;(&quot; attr(href) &quot;)&quot;;  
font-size: smaller;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>counter-increment Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>counter-increment</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>&lbrack; <i>&lt;identifier&gt;</i> <i>&lt;integer&gt;</i>? &rbrack;+ &vert; none</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>User agent--dependent</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>With this property, counters can be incremented (or decremented) by any value, 
	  positive or negative or 0. If no <i>&lt;integer&gt;</i> is supplied, it defaults to 1.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
h1 {counter-increment: section;}
&ast;.backward li {counter-increment: counter −1;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>counter-reset Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>counter-reset</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>&lbrack; <i>&lt;identifier&gt;</i> <i>&lt;integer&gt;</i>? &rbrack;+ &vert; none </td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>User agent--dependent </td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>With this property, counters can be reset (or set for the first time) to any value, 
	  positive or negative. If no <i>&lt;integer&gt;</i> is supplied, it defaults to 0.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
h1 {counter-reset: section;} h2 {counter-reset:     
subsec 1;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3><b>cursor</b>    <b>Inh. Y Anim. N</b></h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>cursor</h3></th>
	  <th align="right"><h3>Inh. Y Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>&lbrack; <i>&lt;uri&gt;</i> &lbrack; <i>&lt;number&gt;</i> <i>&lt;number&gt;</i> &rbrack;?,&rbrack;&ast; 
	  &lbrack; auto &vert; default &vert; none &vert; context-menu &vert; help &vert; pointer &vert; 
	  progress &vert; wait &vert; cell &vert; crosshair &vert; text &vert; vertical-text &vert; 
	  alias &vert; copy &vert; move &vert; no-drop &vert; not-allowed &vert; e-resize &vert; n-resize 
      &vert; ne-resize &vert; nw-resize &vert; s-resize &vert; se-resize &vert; sw-resize &vert; w-resize 
      &vert; ew-resize &vert; ns-resize &vert; nesw-resize &vert; nwse-resize &vert; col-resize &vert; 
	  row-resize &vert; allscroll &rbrack;</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>auto</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>For <i>&lt;uri&gt;</i> values, given that a <i>&lt;uri&gt;</i> resolves to a supported file type, 
	  a single absolute URI with optional <i>x</i>,<i>y</i> coordinates; otherwise, as declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the cursor shape to be used when a mouse pointer is placed within the 
	  boundary of an element. Authors are cautioned to remember that users are typically 
	  very aware of cursor changes and can be easily confused by changes that seem counter 
	  intuitive. For example, making any noninteractive element switch the cursor state to 
	  pointer is quite likely to cause user frustration. Note that the value syntax makes 
	  URI values optional, but the keyword mandatory. Thus, you can specify any number of 
	  URIs to external cursor resources, but the value <i>must</i> end with a keyword. Leaving 
	  off the keyword will cause conforming user agents to drop the declaration entirely. 
	  CSS3 allows two numbers to be supplied with a <i>&lt;uri&gt;</i> value. These define the 
	  <i>x</i>,<i>y</i> coordinates of the cursor's "active point"; that is, the point in the cursor 
	  that is used for determining hover states, active actions, and so forth. If no numbers 
	  are supplied and the cursor image has no "intrinsic hotspot" (to quote the specification), 
	  the top-left corner of the image is used (equivalent to 0 0). Note that the numbers are 
	  unitless and are interpreted relative to the "cursor's coordinate system" (to quote again).</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
a.moreinfo {cursor: help;}
a&lbrack;href&rbrack;.external {cursor: url(globe.png), auto;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3><b>direction</b>  <b>Inh. Y Anim. Y</b></h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>direction</h3></th>
	  <th align="right"><h3>Inh. Y Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>

<b>Values</b>    ltr &vert; rtl  
<b>Initial</b>     ltr 
<b>value</b>
<b>Computed value</b>   As declared 
<b>Applies</b>     All elements
<b>to</b> 
 Defines the base writing direction of blocks and    
 <b>Description</b>  the direction of embeddings and overrides for the   
 Unicode Bidirectional Algorithm (sometimes called   
<i>bidi</i>). Furthermore, it changes the way a number of properties and
layout decisions are handled, including but not limited to the
placement of table cells in a table row and the layout algorithms for
block boxes.

For a variety of reasons, authors are strongly encouraged to use the
HTML attribute dir rather than the CSS property direction. User agents
that do not support bidirectional text are permitted to ignore this
property.

<p><b>Examples</b></p>
<pre>
&ast;:lang(en) {direction: ltr;}
&ast;:lang(ar) {direction: rtl;}
&lbrack; <i>&lt;display-outside&gt;</i> ‖ <i>&lt;display-inside&gt;</i> &rbrack; &vert;
<i>&lt;displaylistitem&gt;</i> &vert; <i>&lt;display-internal&gt;</i> &vert; <i>&lt;display-box&gt;</i>
&vert;
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3><b>display</b>  <b>Inh. N Anim. N</b></h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>display</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>

<b>Values</b>
<i>&lt;display-legacy&gt;</i>
<b>Definitions</b>
<i><b>&lt;display-outside&gt;</b></i>block &vert; inline &vert; run-in
<i><b>&lt;display-inside&gt;</b></i> flow &vert; flow-root &vert; table &vert; flex &vert; grid &vert;
ruby
<i><b>&lt;display-listitem&gt;</b></i>list-item && <i>&lt;display-outside&gt;</i>? && &lbrack; flow
&vert; flowroot &rbrack;?
<i><b>&lt;display-internal&gt;</b></i>table-row-group &vert; table-header-group &vert;
table-

     footer-group &vert; table-row &vert; table-cell &vert;
     tablecolumn-group &vert; table-column &vert; table-caption &vert;
     ruby-base &vert; ruby-text &vert; ruby-base-container &vert;
     ruby-text-container
</b><i>&lt;display-box&gt;</i></b> contents &vert; none

</b><i>&lt;display-legacy&gt;</i></b>   inline-block &vert; inline-list-item &vert; inline-table &vert;
     inline-flex &vert; inline-grid
<b>Initial value</b>  inline
<b>Computed value</b> As declared
<b>Applies to</b>     All elements
<b>Description</b> Defines the kind of display box an element generates
during layout. Gratuitous use of display with a document type such as
HTML can be tricky, as it upsets the display hierarchy already defined
in HTML, but it can also be very useful. In the case of XML, which has
no such built-in visual hierarchy, display is indispensable.

The value none is often used to make elements "disappear," since it
removes the element and all of its descendant elements from the
presentation. This is true not just in visual media, but in all media;
thus, setting an element to display: none will prevent it from being
spoken by a speaking browser.

The value run-in was long a part of CSS2.1 but was dropped in early
2011 because of inconsistencies among browsers. Despite this, it is
still listed as part of CSS3.

<p><b>Examples</b></p>
<pre>
h1 {display: block;}
li {display: list-item;} img {display: inline;} .hide {display: none;}
tr {display: table-row;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3><b>empty-cells</b>  <b>Inh. Y Anim. N</b></h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>empty-cells</h3></th>
	  <th align="right"><h3>Inh. Y Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>

<b>Values</b>    show &vert; hide
<b>Initial</b>     show
<b>value</b>      
<b>Computed</b>    As declared 
<b>value</b>      
<b>Applies</b>     Elements with the display value table-cell  
<b>to</b> 
 Defines the presentation of table cells that
<b>Description</b>  contain no content. If shown, the cell's borders    
and background are drawn. This property is only     
honored if border-collapse is set to separate; 
otherwise, it is ignored.   
<p><b>Example</b></p>
<pre>
th, td {empty-cells: show;} 
</pre>

<p><b>Note</h5> empty-cells has no effect unless the value of border-collapse is separate.
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3><b>filter</b>    <b>Inh. N Anim. Y</b></h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>filter</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
img.oldschool {filter: sepia(0.9);} h2.glowshadow   
{filter:    
drop-shadow(0 0 0.5em yellow) drop-shadow(0.5em     
0.75em 30px gray);} div.logo {filter:  
url(/assets/filters.svg#spotlight);}
</pre>
      </td>
	</tr>
  </tbody>
</table>

<b>Values</b>    &lbrack; none &vert; blur() &vert; brightness() &vert; contrast() &vert;  
dropshadow() &vert; grayscale() &vert; hue-rotate() &vert; 
invert() &vert; opacity() &vert; sepia() &vert; saturate() &vert;   
url() &rbrack;#   
<b>Initial</b>     none
<b>value</b>      
<b>Computed</b>    As declared 
<b>value</b>      
<b>Applies</b>     All elements (in SVG, applies to all graphics  
<b>to</b>  elements and all container elements except the defs 
element)    
Applies a visual filter to the element, resulting   
<b>Description</b>  in an alteration of its final appearance. url()     
values point to filter elements in SVG files,  
either externally or embedded within the HTML  
document. SVG filters can be quite complex and 
powerful.   
<p><b>Examples</b></p>
<pre>
img.oldschool {filter: sepia(0.9);} h2.glowshadow   
{filter:    
drop-shadow(0 0 0.5em yellow) drop-shadow(0.5em     
0.75em 30px gray);} div.logo {filter:  
url(/assets/filters.svg#spotlight);}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3><b>flex</b>   <b>Inh. N Anim. P</b></h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>flex</h3></th>
	  <th align="right"><h3>Inh. N Anim. P</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>

<b>Values</b>&lbrack; <i>&lt;flex-grow&gt;</i> <i>&lt;flex-shrink&gt;</i>?
    <i>&lt;flex-basis&gt;</i> &rbrack; &vert; none
<b>Initial value</b> 0 1 auto
<b>ComputedRefer to individual properties
  value</b>   
<b>Percentages</b>   Valid for the flex-basis value only, relative to the
    element's parent's inner main axis size
<b>Applies to</b>    Flex items (children of flex containers)
<b>Animatable</b>    Refer to individual flex properties to see which are
    animatable
<b>Description</b>   A shorthand property encompassing the flex-grow,
    flex-shrink, and flex-basis properties, used to set
    the proportion and types of flexibility permitted
<p><b>Examples</b></p>
for a flex item. The minimum valid value is a flex   
basis on its own, in which case the growth and  
<b>Note</b> shrink factors are set to their defaults of 0 and 1, 
<b>flex-basis</b>   respectively. Including the growth and shrink
   factors is optional, but if one is included, the     
   other <i>must</i> also be present.
<pre>
/&ast; sets grow at 1, shrink at 0, basis at auto &ast;/   
nav ul li {flex: 1 0 auto;}  
/&ast; sets grow at 0, shrink at 1, basis at 50% &ast;/    
ol.gallery li {flex: 50%;} #invalid {flex: 1 33.%;}  
/&ast; INVALID &ast;/ 
</pre>
It is <i>strongly</i> recommended that authors use this   
property instead of the separate properties it  
encompasses. 
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>flex-basis  Inh. N Anim. P</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>flex-basis </h3></th>
	  <th align="right"><h3>Inh. N Anim. P</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>

Values     content &vert; &lbrack; <i>&lt;length&gt;</i> &vert; <i>&lt;percentage&gt;</i> &vert;    
   auto &rbrack; 
Initial value     auto 
Computed value    As declared, with length values made absolute
Percentages     Relative to the flex container's inner main axis size    
Applies to   
 Flex items (children of flex containers)     
 
Animatable  <i>&lt;length&gt;</i> and <i>&lt;percentage&gt;</i> values only
   
Description  Defines the initial size of a flex item, used as a 
   basis for all subsequent flex sizing calculations.   
   This can override an explicitly assigned width value 
   for the element.     
<p><b>Examples</b></p>
<pre>
nav ul li {flex-basis: 50%;} ol.gallery li   
   {flex-basis: 300px;} div span.whatevs {flex-basis:   
   auto;}  
</pre>
Note  It is <i>strongly</i> recommended that instead of this    
   property, authors use the flex shorthand property to 
   set an item's flex basis.    
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>flex-direction Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>flex-direction</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Value</b></td>
	  <td>row &vert; row-reverse &vert; column &vert; column-reverse</td>
	</tr>
    <tr>
	  <td><b>Initial value</b></td>
	  <td>row</td>
	</tr>
    <tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
	</tr>
    <tr>
	  <td><b>Applies to</b></td>
	  <td>Flex containers</td>
	</tr>
    <tr>
	  <td><b>Description</b></td>
	  <td>flowed into the flex container, which in turn defines how the flex lines will fill the flex container.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
div.gallery {display: flex; flex-direction: row;}   
section.appetizers {display: flex; flex-direction:  
column;}    
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!-- <h3>flex-flow  Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>flex-flow</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td><i>&lt;flex-direction&gt;</i> ‖ <i>&lt;flex-wrap&gt;</i></td>
	</tr>
	  <td><b>Initial value</b></td>
	  <td>row nowrap</td>
    </tr>
	</tr>
	  <td><b>Computed As value</b></td>
	  <td>As declared</td>
    </tr>
	</tr>
	  <td><b>Applies to</b></td>
	  <td>Flex containers</td>
    </tr>
	</tr>
	  <td><b>Description</b></td>
	  <td>A shorthand property encompassing the flexdirection and flex-wrap properties. Note that the default wrapping value is nowrap (see flex-wrap).</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
div.gallery {display: flex; flex-flow: row wrap;}   
nav.sidenav {display: flex; flex-flow: column nowrap;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>flex-grow  Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>flex-grow</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>

Values    <i>&lt;number&gt;</i>
Initial value    0   
Computed value   As declared 
Applies to     Flex items (children of flex containers)    
     
 Sets the <i>growth factor</i> for a flex item. The value 
Description  Sets the <i>growth factor</i> for a flex item. The value 
  supplied is summed up with all the growth factors of the flex items in the same flex line, 
 and the amount they grow is scaled in proportion to their growth factors as a percentage of the whole. 

<p><b>Examples</b></p>
<pre>
nav ul li {flex-grow: 1;}

ol.gallery li {flex-grow: 0;} /&ast; NO growing &ast;/ div span.whatevs
{flex-grow: 0.5;}
</pre>
Note It is <i>strongly</i> recommended that instead of this property, authors use the flex shorthand property to set an item's flex
growth factor.
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--   <h3>flex-shrink  Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>flex-shrink</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>

Values    <i>&lt;number&gt;</i>
Initial     1   
value      
Computed    As declared 
value      
Applies     Flex items (children of flex containers)    
to 
     Sets the <i>shrink factor</i> for a flex item. The value 
Description  supplied is summed up with all the shrink factors   
of the other flex items in the same flex line, and  
the amount they shrink is scaled proportional to    
their shrink factors as a percentage of the whole.  
<p><b>Examples</b></p>
<pre>
nav ul li {flex-shrink: 0;} /&ast; NO shrinking &ast;/    
ol.gallery li {flex-shrink: 0.5;} div span.whatevs  
{flex-shrink: 1;}   
</pre>
Note It is <i>strongly</i> recommended that instead of this   
property, authors use the flex shorthand property   
to set an item's flex shrink factor.
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>flex-wrap Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>flex-wrap</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values nowrap &vert; wrap &vert; wrap-reverse
Initial value nowrap
Computed value As declared
Applies to Flex containers
Description Defines whether flex items can wrap to multiple flex
lines, or only a single flex line is allowed. In a way, it is analogous
to white-space wrapping in text content. Note, however, that the default
is nowrap, so flex items will keep going in a single line (either a row
or a column) even if that means they continue outside the flex
container. If you want your flex items to wrap to a new flex line when
they run out of room (as in an image gallery), make sure to wrap them.

<p><b>Examples</b></p>
<pre>
 div.gallery {display: flex; flex-wrap: wrap;} nav.sidenav
{display: flex; flex-wrap: nowrap;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>float  Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>float</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values left &vert; right &vert; none
Initial value none
Computed value As declared
Applies to All elements
Description Defines the direction in which an element is floated.
This has traditionally been applied to images in order to let text flow
around them, but in CSS, any element may be floated. A floated element
will generate a block-level box no matter what kind of element it may
be. Floated nonreplaced elements should be given an explicit width, as
they otherwise tend to become as narrow as possible. Floating is
generally well supported by all browsers, but the nature of floats can
lead to unexpected results when they are used as a page layout
mechanism. This is largely due to subtle differences in the
interpretation of statements like "as narrow as possible."

<p><b>Examples</b></p>
<pre>
img.figure {float: left;}
p.sidebar {float: right; width: 15em;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>font Inh. Y Anim. P</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>font</h3></th>
	  <th align="right"><h3>Inh. N Anim. P</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values    &lbrack;&lbrack; <i>&lt;font-style&gt;</i> ‖ &lbrack; normal &vert; small-caps &rbrack;  
 ‖ <i>&lt;fontweight&gt;</i> &rbrack;? <i>&lt;font-size&gt;</i> &lbrack; / 
 <i>&lt;line-height&gt;</i> &rbrack;? <i>&lt;fontfamily&gt;</i>&rbrack; &vert; caption 
 &vert; icon &vert; menu &vert; message-box &vert; small-caption &vert;  
 status-bar  
Initial     Refer to individual properties 
 value      
Computed    See individual properties (font-style, etc.)
 value      
      Calculated with respect to the parent element for   
Percentages  <i>&lt;font-size&gt;</i> and with respect to the element's   
 <i>&lt;fontsize&gt;</i> for <i>&lt;line-height&gt;</i>
Applies     All elements
 to 
  Refer to individual font properties to see which    
Animatable  are animatable 
 </i>     A shorthand property used to set all the aspects of 
 Description  an element's font at once. It can also be used to   
 set the element's font to match an aspect of the    
 user's computing environment using keywords such as 
 icon. If keywords are not used, the minimum font    
 value <i>must</i> include the font size and family in   
 that order, and any font value that is not a  
 keyword must end with the font family. Otherwise,   
 the font declaration will be ignored.  
<p><b>Examples</b></p>  
<pre>
p {font: small-caps italic bold small/ 
1.25em Helvetica,sans-serif;}  
p.example {font: 14px Arial;} /&ast; technically  
correct, although generic font-families are 
encouraged for fallback purposes &ast;/
.figure span {font: icon;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>font-family Inh. Y Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>font-family</h3></th>
	  <th align="right"><h3>Inh. Y Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values    &lbrack; <i>&lt;family-name&gt;</i> &vert; <i>&lt;generic-family&gt;</i> &rbrack;#    
Initial     User agent--specific
value      
Computed    As declared 
value      
Applies to 
All elements   

Description Defines a font family to be used in the display of an
element's text. Note that use of a specific font family (e.g., Geneva)
is wholly dependent on that family being available, either on the user's
computer or thanks to a downloadable font file, and the font family
containing the glyphs needed to display the content. Therefore, using
generic family names as a fallback is strongly encouraged. Font names
that contain spaces or nonalphabetic characters should be quoted to
minimize potential confusion. In contrast, generic fallback family names
should never be quoted.

<p><b>Examples</b></p>
<pre>
p {font-family: Helvetica, Arial, sans-serif;} li
{font-family: Georgia, Times, TimesNR,
&quot;New Century Schoolbook&quot;, serif;} pre {font-family: Consolas,
&quot;Courier New&quot;, &quot;Andale Mono&quot;, Monaco, monospace;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>font-feature-settings Inh. Y Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>font-feature-settings</h3></th>
	  <th align="right"><h3>Inh. Y Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values     normal &vert; <i>&lt;feature-tag-value&gt;</i>&#35;  
Initial value normal
Computed value    As declared  
Applies to     All elements 
 Used to turn font features on and off; examples
Description  include ligatures, old-style numbers, and more.
   Whether a font feature actually can be enabled
   depends entirely on the font face being used:
   turning ligatures on or off can only work if the
   face has defined ligatures in the first place.
<p><b>Examples</b></p>
<pre>
h1 {font-feature-settings: &quot;liga&quot;;}
ol {font-feature-settings: &quot;liga&quot; on, &quot;smcp&quot; on, 
&quot;zero&quot; on;}
</pre>
<p><b>Note</h5>  Has a corresponding &#64;font-face descriptor.
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>font-kerning Inh. Y Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>font-kerning</h3></th>
	  <th align="right"><h3>Inh. Y Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values    auto &vert; normal &vert; none 
Initial     auto
value      
Computed    As declared 
value      
Applies     All elements
to 
     In effect, allows the author to disable kerning of  
Description  text for a given element. The default of auto tells 
user agents to do what they normally do, whatever   
that is. normal directs the user agent to use any   
kerning information in the font face to kern text,  
even if it normally wouldn't. With none, kerning is 
disabled, even if the face has kerning information  
and the user agent would make use of it. Note that  
kerning is done before any letter spacing is 
altered (see letterspacing).
<p><b>Examples</b></p>
<pre>
body {kerning: normal;} div.typewriter {kerning:    
none;} 
</pre>

Note Has a corresponding &#64;font-face descriptor. 
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>font-size Inh. Y Anim. P</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>font-size</h3></th>
	  <th align="right"><h3>Inh. Y Anim. P</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values xx-small &vert; x-small &vert; small &vert; medium &vert; large &vert;  
x-large &vert; xx-large &vert; smaller &vert; larger &vert; 
<i>&lt;length&gt;</i> &vert;     
     
<i>&lt;percentage&gt;</i>    
Initial  medium 
value     
Computed For length values, the absolute length; otherwise,  
value as declared 
  Calculated with respect to the parent element's     
Percentages  font size   
Applies to  All elements
Animatable  <i>&lt;length&gt;</i> and <i>&lt;percentage&gt;</i> values only  
  Defines the size of the font. The size can be  
Description  defined as an absolute size, a relative size, a     
length value, or a  

percentage value. Negative length and percentage values are not
permitted. The dangers of font size assignment are many and varied,
and use of points is particularly discouraged in web design as there
is no certain relationship between points and the pixels on a screen.
It's a matter of historical interest that because of early
misunderstandings, setting the font-size to medium led to different
results in early versions of Internet Explorer and Navigator 4.x.

<p><b>Examples</b></p>
<pre>
h2 {font-size: 200%;}
code {font-size: 0.9em;}
p.caption {font-size: 9px;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>font-size-adjust Inh. Y Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>font-size-adjust</h3></th>
	  <th align="right"><h3>Inh. Y Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values <i>&lt;number&gt;</i> &vert; none
Initial value none
ComputedAs declared value
Applies to    All elements
Description   Defines an aspect value for the element, which is
    used to scale fonts such that they more closely match
    each other in cases where fallback fonts are used. The
    proper aspect value for a font is its true xheight
    divided by its font size.

<p><b>Examples</b></p>
<pre>
body {font-family: Helvetica, sans-serif;
font-size-adjust: 0.53;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>font-stretch Inh. Y Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>font-stretch</h3></th>
	  <th align="right"><h3>Inh. Y Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values normal &vert; ultra-condensed &vert; extra-condensed &vert; condensed &vert;
semi-condensed &vert; semi-expanded &vert; expanded &vert; extra-expanded &vert;
ultra-expanded
Initial value normal Computed value As declared
Applies to All elements
Description Replaces a given font face with a narrower or wider
variant, but only if the face has narrower or wider variants defined.
User agents will not programmatically stretch or squeeze a face, but
only swap in a variant face (if it exists).

<p><b>Examples</b></p> h1.bigtext {font-stretch: ultra-expanded;} caption.meme
{font-stretch: condensed;} Note Has a corresponding &#64;font-face
descriptor.
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>font-style  Inh. Y Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>font-style</h3></th>
	  <th align="right"><h3>Inh. Y Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values    italic &vert; oblique &vert; normal 
Initial     normal 
value      
Computed    As declared 
value      
Applies     All elements
to 
     Defines whether the font uses an italic, oblique,   
Description  or normal font face. Italic text is generally  
defined as a separate face within the font family.  
It is theoretically possible for a user agent to    
compute a slanted font face from the normal face.   
In reality, user agents rarely (if at all)  
recognize the difference between italic and oblique 
text and almost always render both in exactly the   
same way.   
<p><b>Examples</b></p>
<pre>
em {font-style: oblique;} i {font-style: italic;}
</pre>
Note Has a corresponding &#64;font-face descriptor. 
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>font-synthesis Inh. Y Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>font-sythesis</h3></th>
	  <th align="right"><h3>Inh. Y Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values none &vert; &lbrack; weight ‖ style &rbrack;
Initial value weight style Computed value As declared
Applies to All elements
Description Defines whether user agents are permitted to
programmatically generate bold or italic variants for

fonts that don't have bold or italic faces. This is generally frowned
upon by typographers, and the results can be visually displeasing, but
it does permit visual emphasis of text in font families that lack the
necessary faces. If you don't want to risk it, use none to suppress
this behavior.

<p><b>Examples</b></p>
<pre>
h1 {font-synthesis: none;}
pre code {font-synthesis: style;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!-- <h3>font-variant Inh. Y Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>font-variant </h3></th>
	  <th align="right"><h3>Inh. Y Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values  normal &vert; small-caps 
 (CSS2.1)     
Values  normal &vert; none &vert; &lbrack; <i>&lt;common-lig-values&gt;</i> ‖  
 (Level 3)    
   <i>&lt;discretionary-lig-values&gt;</i> ‖     
   <i>&lt;historical-lig-values&gt;</i> ‖
   <i>&lt;contextual-alt-values&gt;</i> ‖
   stylistic(<i>&lt;featurevalue-name&gt;</i>) ‖ 
   historical-forms ‖   
   styleset(<i>&lt;feature-value-name&gt;</i>#) ‖
   charactervariant(<i>&lt;feature-value-name&gt;</i>#) ‖
   swash(<i>&lt;featurevalue-name&gt;</i>) ‖     
   ornaments(<i>&lt;feature-value-name&gt;</i>) ‖
   annotation(<i>&lt;feature-value-name&gt;</i>) ‖ &lbrack; smallcaps  
   &vert; all-small-caps &vert; petite-caps &vert; allpetite-caps   
   &vert; unicase &vert; titling-caps &rbrack; ‖ 
   <i>&lt;numeric-figure-values&gt;</i> ‖
   <i>&lt;numeric-spacingvalues&gt;</i> ‖
   <i>&lt;numeric-fraction-values&gt;</i> ‖ ordinal ‖    
   slashed-zero ‖ <i>&lt;east-asian-variant-values&gt;</i> ‖     
   
   <i>&lt;east-asian-width-values&gt;</i> ‖ ruby &rbrack; 
Initial normal  
 value   
Computed     As declared  
 value   
Applies All elements 
 to   
Defines whether text is set in the small-caps style. 
Description  It   
is theoretically possible for a user agent to compute a small-caps
font face from the normal face.

<p><b>Examples</b></p>
<pre>
h3 {font-variant: small-caps;} p {font-variant: normal;}
</pre>
Note Has a corresponding &#64;font-face descriptor.
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>font-weight Inh. Y Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>font-weight</h3></th>
	  <th align="right"><h3>Inh. Y Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values    normal &vert; bold &vert; bolder &vert; lighter &vert; 100 &vert; 200   
&vert; 300 &vert; 400 &vert; 500 &vert; 600 &vert; 700 &vert; 800 &vert; 900    
Initial     normal 
value      
Computed    One of the numeric values (100, etc.), or one of    
value  the numeric values plus one of the relative values  
(bolder or lighter) 
Applies     All elements
to 
     Defines the font weight used in rendering an
Description  element's text. The numeric value 400 is equivalent 
to the keyword normal, and 700 is equivalent to     
bold. If a font has only two weights---normal and   
bold--- the numbers 100 through 500 will be normal, 
and 600 through 900 will be bold. In general terms, 
the visual result of each numeric value must be at  
least as light as the next lowest number and at     
least as heavy as the next highest number.  
<p><b>Examples</b></p>
<pre>
b {font-weight: 700;} strong {font-weight: bold;}   
.delicate {font-weight: lighter;}   
</pre>
 Note Has a corresponding &#64;font-face descriptor.
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>grid Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>grid</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values none &vert; subgrid &vert; &lbrack; *&lt;grid-template-rows&gt;* /    
*&lt;gridtemplate-columns&gt;* &rbrack; &vert; &lbrack; 
*&lt;line-names&gt;*? *&lt;string&gt; &lt;track-size&gt;*? 
*&lt;line-names&gt;*? &rbrack;+ &lbrack; / *&lt;track-list&gt;* &rbrack;? &vert;  
&lbrack; *&lt;grid-auto-flow&gt;* &lbrack; *&lt;grid-auto-rows&gt;* &lbrack;  
/ *&lt;gridauto-columns&gt;* &rbrack;? &rbrack;? &rbrack; &rbrack; 
Initial  See individual properties   
value     
Computed See individual properties   
value     
Applies to  Grid containers     
*  A shorthand property allowing the almost complete   
*Description 
definition of an element's grid system, not counting
grid gaps. The value syntax can become quite complex and, for
clarity's sake, most authors rely on the individual properties instead
of grid, but there are no technical reasons to avoid grid.

<p><b>Example</b></p> 
<pre>
body {display: grid; grid:
&quot;header header header header&quot; 3em
&quot;. content sidebar .&quot; 1fr
&quot;footer footer footer footer&quot; 5em /
2em 3fr minmax(10em,1fr) 2em;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!-- <h3>grid-area Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>grid-area</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values    *&lt;grid-line&gt;* &lbrack; / *&lt;grid-line&gt;* &rbrack;{0,3}
Initial     See individual properties   
value      
Computed    As declared 
value      
Applies     Grid items and absolutely positioned elements, if   
to  their containing block is a grid container  
*     Used to assign a grid item to a specific area of a  
*Description  defined grid. This can be done using a single  
identifier, or using slash-separated grid line 
identifiers. If all four grid lines are supplied,   
they are given in the order row-start (top) /  
column-start (left) / row-end (bottom) / column-end 
(right), which is the reverse of the usual  
top-right-bottom-left order for margins, padding,   
and so on.  
<p><b>Examples</b></p>
<pre>
#masthead {grid-area: header;} 
#sidebar {grid-area: 1 / 2 / 1 / 3;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>grid-auto-columns Inh. N Anim. N</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3> </h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values *&lt;track-breadth&gt;* &vert; minmax(*&lt;track-breadth&gt;*,
*&lt;trackbreadth&gt;*)
Definition
*&lt;track-breadth&gt; &lt;length&gt;* &vert; *&lt;percentage&gt;* &vert; *&lt;flex&gt;* &vert;
min-content &vert;
max-content &vert; auto
Initial value auto
Depends on the specific track sizing
Grid containers
Description Defines the sizing of column tracks for columns that are
automatically generated; that is, columns that are created because a
grid item needs to be placed outside the explicitly defined grid
columns.
<p><b>Example</b></p>
<pre>
div.grid {display: grid;
grid-template-rows: 80px 80px; grid-template-columns: 20em 1fr;
grid-auto-columns: 20em;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>grid-auto-flow Inh. N Anim. N</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3> </h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values &lbrack; row &vert; column &rbrack; ‖ dense
Initial value row
Computed value As declared
Applies to Grid containers
Description Defines the direction in which grid items that have not
been explicitly assigned to a grid area using grid-area or the
grid-column and grid-row properties will be automatically flowed into
the grid container.

<p><b>Examples</b></p>
<pre>
section.menu {grid-auto-flow: column;}
div.gallery {grid-auto-flow: row dense;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>grid-auto-rows Inh. N Anim. N</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3> </h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values   *&lt;track-breadth&gt;* &vert; minmax(*&lt;track-breadth&gt;*,   
 *&lt;trackbreadth&gt;*)  
 *&lt;length&gt;* &vert; *&lt;percentage&gt;* &vert; *&lt;flex&gt;* &vert;    
Definition  min-content &vert; max-content &vert; auto   
*&lt;track   
-breadth&gt;*  
Initial    auto 
value      
Computed   Depends on the specific track sizing 
value      
Applies      
to Grid      
containers     
Description Defines the sizing of row tracks for rows that are
automatically generated; that is, rows that are created because a grid
item needs to be placed outside the explicitly defined grid rows.
<p><b>Example</b></p>
<pre>
div.grid {display: grid;
grid-template-rows: 80px 80px; grid-template-columns: 20em 1fr;
grid-auto-rows: 80px;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>grid-column Inh. N Anim. N</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3> </h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values     *&lt;grid-line&gt;* &lbrack; / *&lt;grid-line&gt;* &rbrack;?     
Definition  
*&lt;g auto &vert; *&lt;identifier&gt;* &vert; &lbrack; *&lt;integer&gt;* && 
rid-line&gt;*  *&lt;identifier&gt;*? &rbrack; &vert; &lbrack; span && &lbrack; *&lt;integer&gt;*  
   &vert;&vert; *&lt;identifier&gt;* &rbrack; &rbrack;  
Initial auto 
value   
Computed     As declared  
value   
Applies Grid items and absolutely positioned elements, if    
to   their containing block is a grid container   
     Acts as a shorthand property encompassing the
Description  grid-column-start and grid-column-end properties.    
   When a single number or identifier is given, the     
   second is assumed to be the span 1 (for a number) or 
   the same identifier. Negative numeric grid lines     
   count backward from the end of the explicit grid     
   (generally the right side).  
<p><b>Examples</b></p>
<pre>
header {grid-column: 1 / -1;}
&pound;sidebar {grid-column: 1 / span 2;} 
footer {grid-column: footer / 4;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>grid-column-end Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>grid-column-end</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values auto &vert; *&lt;custom-ident&gt;* &vert; &lbrack; *&lt;integer&gt;* && *&lt;custom-*
*ident&gt;*? &rbrack; &vert; &lbrack; span && &lbrack; *&lt;integer&gt;* ‖ *&lt;customident&gt;* &rbrack;&rbrack;
Initial value auto
As declared
Grid items and absolutely positioned elements, if their containing
block is a grid container
Description Defines the column grid line on which an element's
layout ends, or (when using the span keyword) the number of column
tracks, or identified column tracks, the element spans.
<p><b>Examples</b></p>
<pre>
header {grid-column-end: main-content;}
#sidebar {grid-column-end: span 2;} footer {grid-column-end: 4;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>grid-column-gap Inh. N Anim. Y  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>grid-column-gap</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values *&lt;length&gt;* &vert; *&lt;percentage&gt;*
Initial value 0
Computed value An absolute length
Applies to Grid containers
Description Sets a gap distance between column tracks. This permits
an author to force open gaps between column tracks, even when the grid
items have no margins to push them away from each other. The gap size is
the same for all column gaps.
<p><b>Example</b></p>
<pre>
#grid {display: grid; grid-column-gap: 1em;}
</pre>
Note As of early 2018, the CSS Working Group intends to change this
property to simply column-gap and have it apply to multicolumn and flex
containers as well as grid containers.
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>grid-column-start Inh. N Anim. N  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>grid-column-start</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values   auto &vert; *&lt;custom-ident&gt;* &vert; &lbrack; *&lt;integer&gt;* &&    
   *&lt;customident&gt;*? &rbrack; &vert; &lbrack; span && &lbrack; *&lt;integer&gt;* 
   ‖ *&lt;customident&gt;* &rbrack;&rbrack;     
Initial    auto 
value      
Computed     
value As     
declared  

Applies to Grid items and absolutely positioned elements, if their
containing block is a grid container

Description Defines the column grid line on which an element's
layout starts, by means of either a grid line number or an identifier.
If the span keyword is used, the grid item spans back from the grid line
defined by gridcolumn-end.

<p><b>Examples</b></p>
<pre>
header {grid-column-start: masthead;}
#sidebar {grid-column-start: span 1;} footer {grid-column-start: -2;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>grid-gap  Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>grid-gap</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values    *&lt;grid-row-gap&gt;* *&lt;grid-column-gap&gt;*    
Initial     0 0 
value      
Computed    As declared 
value      
Applies     Grid containers     
to 
*     A shorthand property encompassing the grid-rowgap   
*Description  and grid-column-gap properties, in that order. If   
only one value is supplied, the value is assumed to 
be the same for both row and column gaps.   
<p><b>Examples</b></p>
<pre>
#grid {display: grid; grid-gap: 12px 1em;}
div.gallery {display: grid; grid-gap: 2.5vw;}
</pre>
Note As of early 2018, the CSS Working Group intends to  
change this property to simply gap and have it 
apply to multicolumn and flex containers as well as 
grid containers.
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>grid-row  Inh. N Anim. N</h3> -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>grid-row</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values *&lt;grid-line&gt;* &lbrack; / *&lt;grid-line&gt;* &rbrack;?
Definition
*&lt;grid-line&gt;* auto &vert; *&lt;identifier&gt;* &vert; &lbrack; *&lt;integer&gt;* &&
*&lt;identifier&gt;*? &rbrack; &vert;

&lbrack; span && &lbrack; *&lt;integer&gt;* &vert;&vert; *&lt;identifier&gt;* &rbrack; &rbrack;
Initial value auto
As declared

Grid items and absolutely positioned elements, if their containing
block is a grid container

Description Acts as a shorthand property encompassing the
grid-row-start and grid-row-end properties. When a single number or
identifier is declared, the second is assumed to be the span 1 (for a
number) or the same identifier.

<p><b>Examples</b></p>
<pre>
#sidebar {grid-row: 1 / -1;}
footer {grid-row: footer-start / footer-end;}f
header {grid-row: top;} /&ast; a trailing &apos;/ span 1&apos; is assumed &ast;/
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>grid-row-end Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>grid-row-end</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Valuesauto &vert; *&lt;custom-ident&gt;* &vert; &lbrack; *&lt;integer&gt;* &&
    *&lt;customident&gt;*? &rbrack; &vert; &lbrack; span && &lbrack; *&lt;integer&gt;* ‖
    *&lt;customident&gt;* &rbrack;&rbrack;
Initial value auto
ComputedAs declared value
Applies to    Grid items and absolutely positioned elements, if
    their containing block is a grid container
Description   Defines the row grid line on which an element's layout
    ends, or (when using the span keyword) the number of
    row tracks, or identified row tracks, the element
    spans across.

<p><b>Examples</b></p>
<pre>
header {grid-row-end: span 1;}
&dollar;sidebar {grid-row-end: -1;} footer {grid-row-end: footer-end;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>grid-row-gap Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>grid-row-gap</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values *&lt;length&gt;* &vert; *&lt;percentage&gt;*
Initial value 0
Computed value An absolute length
Applies to Grid containers
Description Sets a gap distance between row tracks. This permits an
author to force open gaps between row tracks, even when the grid items
have no margins to push them away from each other. The gap size is the
same for all row gaps.

<p><b>Example</b></p>
<pre>#grid {display: grid; grid-row-gap: 12px;}</pre>

Note As of early 2018, the CSS Working Group intends to change this
property to simply row-gap and have it apply to multicolumn and flex
containers as well as grid containers.
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>grid-row-start Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>grid-row-start</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Valuesauto &vert; *&lt;custom-ident&gt;* &vert; &lbrack; *&lt;integer&gt;* &&
    *&lt;customident&gt;*? &rbrack; &vert; &lbrack; span && &lbrack; *&lt;integer&gt;* ‖
    *&lt;customident&gt;* &rbrack;&rbrack;
Initial value auto
ComputedAs declared
  value   
Applies to    Grid items and absolutely positioned elements, if
    their containing block is a grid container
Description   Defines the row grid line on which an element's layout
    starts, by means of either a grid line number or an
    identifier. If the span keyword is used, this means
    the grid item spans back from the grid line defined by
    grid-row-end.

<p><b>Examples</b></p>
<pre>
header {grid-row-start: masthead;}
&pound;sidebar {grid-row-start: span 1;}
footer {grid-row-start: footer-start;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>grid-template-areas Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>grid-template-areas</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values none &vert; *&lt;string&gt;*
Initial value none
Computed value As declared
Applies to Grid containers
Description This property allows the author to create an explicit
grid system using strings of text to define the names and placement of
grid areas. This allows for a much more visual representation of the
grid areas in a grid container, and automatically creating named grid
lines to make the grid areas work. Because the areas are defined using
patterns of text, no areas defined with this property can overlap.

<p><b>Examples</b></p> 
<pre>
#grid {display: grid;
grid-template-areas:
&quot;h h h h&quot;
&quot;l c c r&quot;
&quot;l f f f&quot;;}
#grid2 {display: grid; grid-template-areas:
&quot;header header header header&quot;
&quot;leftside content content rightside&quot;
&quot;leftside footer footer footer&quot;;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>grid-template-columns Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>grid-template-columns</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Valuesnone &vert; *&lt;track-list&gt;* &vert; *&lt;auto-track-list&gt;*
Initial value none
ComputedAs declared, with lengths made absolute
  value   
Percentages   Refer to the inline size (usually width) of the grid
    container
Applies to    Grid containers
Description   Provides authors a way to define grid line names and
    track sizes for columns in the explicit grid.
<p><b>Examples</b></p>
<pre>
aside {grid-template-columns:
max-content min-content max-content;} article {grid-template-columns:
15em 4.5fr 3fr 10%;} section {grid-template-columns:
&lbrack;start col-a&rbrack; 200px &lbrack;col-b&rbrack; 50% &lbrack;col-c&rbrack; 1fr
&lbrack;stop end last&rbrack;;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>grid-template-rows Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>grid-template-rows</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values    none &vert; *&lt;track-list&gt;* &vert; *&lt;auto-track-list&gt;*   
Initial     none
value      
Computed    As declared, with lengths made absolute     
value      
*     Refer to the block size (usually height) of the     
*Percentages  grid container 
Applies     Grid containers     
to 
*     Provides authors a way to define grid line names    
*Description  and track sizes for rows in the explicit grid. 
<p><b>Examples</b></p>
<pre>
aside {grid-template-rows: 200px 50% 100px;}
article {grid-template-rows: 3em minmax(5em,1fr)    
2em;} section {grid-template-rows:  
&lbrack;start masthead&rbrack; 3em &lbrack;content&rbrack; calc(100%-5em)   
&lbrack;footer&rbrack; 2em &lbrack;stop end&rbrack;;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>height    Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>height</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values *&lt;length&gt;* &vert; *&lt;percentage&gt;* &vert; auto    
Initial  auto
value     
Computed For auto and percentage values, as declared;
value otherwise, an absolute length, unless the property  
does not apply to the element (then auto)   
*  Calculated with respect to the height of the
*Percentages  containing block (when valid)  
Applies to  All elements except nonreplaced inline elements,    
table rows, and row groups  
*  Defines the total height of portions of an element; 
*Description  the exact portions depend on the value of   
boxsizing. Negative length and percentage values    
are not permitted.  
<p><b>Examples</b></p>
<pre>
img.icon {height: 50px;}    
h1 {height: 1.75em;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>hyphens   Inh. Y Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>hyphens</h3></th>
	  <th align="right"><h3>Inh. Y Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values    manual &vert; auto &vert; none 
Initial value    manual 
Computed value   As declared 
 No  
Animatabale 
Applies to    All elements
 Used to declare whether the hyphenation of words at 
Description  line breaks must be done manually (e.g., with a     
 "soft hyphen"---&shy; or U+00AD---inserted into the 
 document) or can be done automatically by the user  
 agent. In the case of none, all hyphenation is 
 suppressed, even when hinted manually in the
 document. Automatic hyphenation is heavily  
 languagedependent, and may vary greatly between     
 user agents.
<p><b>Examples</b></p>  h1, h2 {hyphens: none;} aside.poem {hyphens:
 manual;}    
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>isolation Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>isolation</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values auto &vert; isolate     
Initial value auto
Computed value     As declared 
Applies to  All elements (in SVG, it applies to container  
 elements, graphics elements, and    
 graphics-referencing elements) 
   Determines whether an element creates an isolated   
Description  blending context. An isolated element will only     
 blend with itself; that is, the foreground portions 
 of the element will blend with the background  
 portions    

of that same element, but *not* with the backdrop of its parent element
or any other elements that might appear behind it. The visual effect can
be similar to that of a document loaded into an iframe element, though
this analogy is not exact: the isolated element still inherits styles
from its ancestors.

<p><b>Example</b></p> p.alone {isolation: isolate;}

<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>justify-content Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>justify-content</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values    flex-start &vert; flex-end &vert; center &vert; space-between   
 &vert; space-around &vert; space-evenly     
Initial value     flex-start  
Computed value   As declared 
Applies to    Flex containers     
 Defines the distribution of flex items along the    
Description  main axis of a flex container. 
<p><b>Examples</b></p>  nav {justify-content: space-evenly;} div.gallery    
 {justify-content: space-between;}   
Note As of early 2018, there are plans to have this 
 property apply to many (or all) elements, not just  
 flex containers, and be given the values start and  
 end to replicate flex-start and flex-end behavior   
 for non-flex environments.
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>left Inh. N Anim. P</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>left</h3></th>
	  <th align="right"><h3>Inh. N Anim. P</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values *&lt;length&gt;* &vert; *&lt;percentage&gt;* &vert; auto    
Initial value auto
  
Computed value     For static elements, auto; for length values, the   
corresponding absolute length; for percentage  
values, the specified value; otherwise, auto
Refer to the height of the containing block for top 
Percentages  and bottom, and the width of the containing block   
for right and left  
Applies to  Positioned elements 
Animatable  *&lt;length&gt;* and *&lt;percentage&gt;* values only  
Description Defines the offset between the left outer margin edge of
an absolutely positioned element and the left edge of its containing
block; or, for relatively positioned elements, the distance by which the
element is offset to the right of its starting position.

<p><b>Examples</b></p>
<pre>
div#footer {position: fixed; left: 0;}
&ast;.hanger {position: relative; left: −25px;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>letter-spacing Inh. Y Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>letter-spacing</h3></th>
	  <th align="right"><h3>Inh. Y Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values    *&lt;length&gt;* &vert; normal 
Initial     normal 
value      
Computed    For length values, the absolute length; otherwise,  
value      
normal 
Applies     All elements
to 
*     Defines the amount of whitespace to be inserted     
 *Description  between the character boxes of text. Because
 character glyphs are typically narrower than their  
 character boxes, length values create a modifier to 
 the usual spacing between letters. Thus, normal is  
 (most likely) synonymous with 0. Negative length    
 and percentage values are permitted and will cause  
 letters to bunch closer together.   
<p><b>Examples</b></p>  
<pre>
p.spacious {letter-spacing: 6px;}
em {letter-spacing: 0.2em;}
p.cramped {letter-spacing: −0.5em;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>line-break Inh. Y Anim. Y  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>line-break</h3></th>
	  <th align="right"><h3>Inh. Y Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values    auto &vert; loose &vert; normal &vert; strict   
Initial     auto
value      
Computed    As declared 
value      
Applies     All elements
to 
*     Affects the wrapping of lines of text in CJK
*Description  (Chinese-Japanese-Korean) text. The precise 
meanings of loose, normal, and strict are left 
unde‐  
fined, so    
the only     
solid     
expectation  
is that      
loose will   
use the      
"least  
restrictive" 
     
line-breaking, 
normal will  
use the      
"most     
common"      
      
 line-breaking, 
 and strict   
 will use the 
 "most     
stringent"   
      
line-breaking. 
     
<p><b>Example</b></p>    
<pre>
div.cjk     
{line-break:   
strict;}  
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>line-height Inh. Y Anim. Y
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3> </h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values *&lt;number&gt;* &vert; *&lt;length&gt;* &vert; *&lt;percentage&gt;* &vert; 
normal 
Initial value normal 
Computed value     For length and percentage values, the absolute 
value; otherwise, as declared  
Relative to the font size of the element    
Percentages 
Applies to  All elements (but see text regarding replaced and   
block-level elements)  
This property influences the layout of line boxes.  
Description  When applied to a block-level element, it defines   
the minimum (but not the maximum) distance between  
baselines within that element. When applied to an   
inline element, it is used to define the *leading*  
of that element.    
     
The difference between the computed values of  
line-height and font-size (called "leading" in CSS) 
is split in half and added to the top and bottom of 
each piece of content in a line of text. The
shortest box that can enclose all those pieces of   
content is the line box.    
     
A raw number value assigns a scaling factor, which  
is inherited instead of a computed value. Negative  
values are not permitted.   
<p><b>Examples</b></p>

<pre>
 p {line-height: 1.5em;}     
h2 {line-height: 200%;} 
ul {line-height: 1.2;} 
pre {line-height: 0.75em;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>list-style Inh. Y Anim. N
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3> </h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values    &lbrack; *&lt;list-style-type&gt;* ‖ *&lt;list-style-image&gt;* ‖ 
*&lt;list-styleposition&gt;* &rbrack; 
Initial value     Refer to individual properties 
Computed value   See individual properties   
Applies to    Elements whose display value is list-item   
 A shorthand property that defines the marker type,  
Description  whether a symbol or an image, and its (crude)  
placement. Because it applies to any element that   
has a display value of list-item, it will apply     
only to li elements in ordinary HTML, although it   
can be applied to any element and subsequently 
inherited by list-item elements.    
<p><b>Examples</b></p>
<pre>
ul {list-style: square url(bullet3.gif) outer;} /&ast; 
values are inherited by &apos;li&apos; elements &ast;/ 
ol {list-style: upper-roman;}  
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>list-style-image Inh. Y Anim. N
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3> </h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>*&lt;uri&gt;* &vert; *&lt;image&gt;* &vert; none</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>none</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>*&lt;uri&gt;* values, the absolute URI; otherwise, none</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>Elements whose display value is list-item</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Specifies an image to be used as the marker on an ordered or unordered list item. The placement of the
image with respect to the content of the list item can be crudely controlled using list-style position.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
ul {list-style-image: url(bullet3.gif);}
ul li {list-style-image:
url(\\http://example.org/pix/checkmark.png);}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>list-style-position Inh. Y Anim. N  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>list-style-position</h3></th>
	  <th align="right"><h3>Inh. Y Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>inside &vert; outside</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>outside</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>Elements whose display value is list-item</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the position of the list marker with respect to
the content of the list item. Outside markers are placed some distance
from the border edge of the list item, but the distance is not defined
in CSS. Inside markers are treated as though they were inline elements
inserted at the beginning of the list item's content.
</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
li {list-style-position: outside;}
ol li {list-style-position: inside;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>list-style-type Inh. Y Anim. N  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>list-style-type</h3></th>
	  <th align="right"><h3>Inh. Y Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>disc &vert; circle &vert; square &vert; disclosure-open &vert;
disclosure-closed &vert; decimal &vert; decimal-leadingzero &vert; arabic-indic &vert;
armenian &vert; upper-armenian &vert; lower-armenian &vert; bengali &vert; cambodian &vert;
khmer &vert; cjk-decimal &vert; devanagari &vert; gujarati &vert; gurmukhi &vert; georgian
&vert; hebrew &vert; kannada &vert; lao &vert; malayalam &vert; mongolian &vert; myanmar &vert;
oriya &vert; persian &vert; lowerroman &vert; upper-roman &vert; tamil &vert; telugu &vert; thai
&vert; tibetan &vert; lower-alpha &vert; lower-latin &vert; upperalpha &vert; upper-latin &vert;
cjk-earthly-branch &vert; cjkheavenly-stem &vert; lower-greek &vert; hiragana &vert;
hiragana-iroha &vert; katakana &vert; katakana-iroha &vert; japanese-informal &vert;
japanese-formal &vert; koreanhangul-formal &vert; korean-hanja-informal &vert;
koreanhanja-formal &vert; simp-chinese-informal &vert; simpchinese-formal &vert;
trad-chinese-informal &vert; tradchinese-formal &vert; ethiopic-numeric &vert;
*&lt;string&gt;* &vert; none</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>disc</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>Elements whose display value is list-item</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the type of marker system to be used in the
presentation of a list. CSS3 provides a greatly expanded number of list
types, but as of early 2018, support for these newer list types has some
spotty parts. Use caution when using list types beyond those provided by
CSS2.1.

There is no defined behavior for what happens when a list using an
alphabetic ordering exceeds the letters in the list. For example, once
an upper-latin list reaches "Z," the specification does not say what
the next bullet should be. (Two possible answers are "AA" and "ZA.")
This is the case regardless of the alphabet in use. Thus, there is no
guarantee that different user agents will act consistently.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
ul {list-style-type: square;}
ol {list-style-type: lower-roman;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>margin    Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>margin</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>&lbrack; *&lt;length&gt;* &vert; *&lt;percentage&gt;* &vert; auto &rbrack;{1,4}</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>Not defined </td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>See individual properties   
Refer to the width of the containing block </td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>A shorthand property that defines the width of the  
 overall margin for an element or sets distinct 
 widths for the individual side margins. Vertically  
 adjacent margins of block-level elements are
 collapsed, whereas inline elements effectively do   
 not take top and bottom margins. The left and right 
 margins of inline elements do not collapse, nor do  
 margins on floated elements. Negative margin values 
 are permitted, but caution is warranted because     
 negative values can cause elements to overlap other elements or to appear to be wider than their parent elements.
</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
h1 {margin: 2ex;}
p {margin: auto;} img {margin: 10px;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>margin-bottom Inh. N Anim. Y  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>margin-bottom</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values*&lt;length&gt;* &vert; *&lt;percentage&gt;* &vert; auto
Initial value 0
ComputedFor length values, the absolute length; otherwise, as
value   declared
Percentages   Refer to the width of the containing block
Applies to    All elements
Description   Defines the width of the bottom margin for an element.
    Negative values are permitted, but caution is
    warranted (see margin).

<p><b>Examples</b></p>
<pre>
ul {margin-bottom: 0.5in;}
h1 {margin-bottom: 2%;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>margin-left Inh. N Anim. Y  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>margin-left</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values*&lt;length&gt;* &vert; *&lt;percentage&gt;* &vert; auto
Initial value 0
ComputedFor length values, the absolute length; otherwise, as
  value   declared
Percentages   Refer to the width of the containing block
Applies to    All elements
Description   Defines the width of the left margin for an element.
    Negative values are permitted, but caution is
    warranted (see margin).

<b>Examples</b>
<pre>
p {margin-left: 5%;}
pre {margin-left: 3em;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>margin-right Inh. N Anim. Y  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>margin-right</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values*&lt;length&gt;* &vert; *&lt;percentage&gt;* &vert; auto
Initial value 0
ComputedFor length values, the absolute length; otherwise, as
value   declared
Percentages   Refer to the width of the containing block
Applies to    All elements
Description   Defines the width of the right margin for an element.
    Negative values are permitted, but caution is
    warranted (see margin).

<p><b>Examples</b></p>
<pre>
img {margin-right: 30px;}
ol {margin-right: 5em;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>margin-top Inh. N Anim. Y  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>margin-top</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values    *&lt;length&gt;* &vert; *&lt;percentage&gt;* &vert; auto    
Initial     0   
value      
Computed    For length values, the absolute length; otherwise,  
value  as declared 
*     Refer to the width of the containing block  
*Percentages 
Applies     All elements
to 
*     Defines the width of the top margin for an element. 
*Description  Negative values are permitted, but caution is  
warranted (see margin).     
<p><b>Examples</b></p>
<pre>
ul {margin-top: 0.5in;} h3 {margin-top: 1.5em;}     
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>mask Inh. N Anim. P  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>mask</h3></th>
	  <th align="right"><h3>Inh. N Anim. P</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values    &lbrack; *&lt;mask-image&gt;* ‖ *&lt;mask-position&gt;* &lbrack; / 
*&lt;masksize&gt;* &rbrack;? ‖ *&lt;mask-repeat&gt;* ‖    
*&lt;mask-clip&gt;* ‖ *&lt;maskorigin&gt;* ‖
*&lt;mask-composite&gt;* ‖ *&lt;mask-mode&gt;* &rbrack;#  
Initial      
value See    
individual     
properties     
Computed As declared 
value     
Applies to  All elements (in SVG, applies to all graphics  
elements and all container elements except the defs 
element)    
Animatable  Refer to individual mask properties to see which    
 are animatable 
 *  A shorthand property encompassing all the other     
 *Description  image masking properties. It is analogous to
 background as compared to the various background    
 properties, and many of the masking and background  
 properties share values and behaviors. 
<p><b>Examples</b></p>
<pre>
img.masked {mask:   
url(#mask) no-repeat center/cover luminance;}
#example {mask: url(c.svg) repeat-y top left / auto subtract, url(s.png)
no-repeat center / 50% 33% add, url(t.gif) repeat-y 25% 67% / contain
add;
}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>mask-clip Inh. N Anim. N  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>mask-clip</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values    &lbrack; content-box &vert; padding-box &vert; border-box &vert; 
 margin-box &vert; fill-box &vert; stroke-box &vert; view-box &vert; 
 no-clip &rbrack;# 
Initial     border-box  
 value      
Computed    As declared 
 value      
Applies     All elements (in SVG, applies to all graphics  
to  elements and all container elements except the defs 
element)    
*     Defines the outer edge of the visible portions of   
*Description  an element's mask, as an aspect of the element's    
box model. This allows authors to apply a masking   
shape to an element but then further reduce the     
visible parts of the element without having to 
directly alter the mask shape. 
<p><b>Examples</b></p>
<pre>
 p:nth-child(1) {mask-clip: border-box;}     
p:nth-child(2) {mask-clip: padding-box;}    
p:nth-child(3) {mask-clip: content-box;}    
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>mask-composite Inh. N Anim. N  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>mask-comnposite</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values&lbrack; add &vert; subtract &vert; intersect &vert; exclude &rbrack;#
Initial value add
Computed value  As declared
Applies to    All elements (in SVG, applies to all graphics elements
    and all container elements except the defs element)
Description   Controls the way multiple masks are combined, with the
    result sometimes dependent on the order of the mask
    shapes. For example, if a square mask is atop a
    circular mask and the value of mask-composite is

subtract, then the circle is subtracted from the square. If the order
is reversed so the circle is atop the square, then the square is
subtracted from the circle. For the other values, the result should
not depend on the masks' stacking order.

<p><b>Examples</b></p>
<pre>
img.masked {mask-composite: add;}
span.mask3 {mask-composite: subtract, add, add;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>mask-image Inh. N Anim. N  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>mask-image</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values   &lbrack; none &vert; *&lt;image&gt;* &vert; *&lt;mask-source&gt;* &rbrack;# 
Any of the value types *&lt;uri&gt;*, *&lt;image()&gt;*,     
 Definitions  *&lt;imageset()&gt;*, *&lt;element()&gt;*,   
 *&lt;cross-fade()&gt;*, or *&lt;gradient&gt;*
   
 *&lt;image&gt;*  
*&lt;mas     A url() that points to a mask element in an SVG 
 k-source&gt;*  image
Initial    none 
 value      
Computed   As declared  
 value      
Applies    All elements (in SVG, applies to all graphics
 to elements and all container elements except the defs  
   element)     
   Applies an image, or a portion of an SVG image, to   
 Description  an element as a masking shape. The result is that    
   the  

masked element has portions of itself made invisible, while others are
wholly or partially visible. The exact visual result will depend on
the value of maskmode; by default, the alpha channel of the maskimage
will be used to determine the masking of the element.

<p><b>Examples</b></p>
<pre>
&ast;.masked.compass {mask-image: url(Compass.png);}
&ast;.masked.theatre {mask-image: url(theatre-masks.svg);}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <!--  <h3>mask-mode Inh. N Anim. N  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>mask-mode</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values&lbrack; alpha &vert; luminance &vert; match-source &rbrack;#
Initial value match-source
ComputedAs declared
value   
Applies to    All elements (in SVG, applies to all graphics elements
    and all container elements except the defs element)
Description   Determines which aspect of a masking image is used to
    determine its masking shape: its transparency or its
    brightness. If alpha is used, then any part of the
    masking image with no transparency reveal the masked
    element, whereas any part of the mask with full
    transparency hides the masked element. Transparency
    values between the two show the masked element, but
    set to the masking image's opacity level. For
    luminance, the brightness of the masking image is
    treated as transparency is for alpha: full brightness
    fully reveals the masked element, full darkness hides
    it, and in-between brightness reveal the masked
    element with some transparency. matchsource means the
    same as alpha *unless* the masking source is an SVG
    mask element, in which case it's the same as
    luminance.

<p><b>Examples</b></p>
<pre>
p {mask-mode: alpha;}
img.lum {mask-mode: luminance, alpha;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <!--  <h3>mask-origin  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>mask-origin</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values&lbrack; content-box &vert; padding-box &vert; border-box &vert;
    margin-box &vert; fill-box &vert; stroke-box &vert; view-box &rbrack;#
Initial value border-box
ComputedAs declared
  value   
Applies to    All elements (in SVG, applies to all graphics elements
    and all container elements except the defs element)
Description   Changes the origin box for the masking image as
    applied to the masked element. This allows the author
    to vary the initial placement of the mask before
    sizing, repeating, or positioning it.

<p><b>Examples</b></p>
<pre>
div.inset {mask-origin: content-box;}
svg#radio {mask-origin: stroke-box, fill-box;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <!--  <h3>mask-position Inh. N Anim. P  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>mask-position</h3></th>
	  <th align="right"><h3>Inh. N Anim. P</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values*&lt;position&gt;*&#35;
Initial value 0% 0%
ComputedAs declared
  value   
Applies to    All elements (in SVG, applies to all graphics elements
    and all container elements except the defs element)
Animatable    *&lt;length&gt;* and *&lt;percentage&gt;* values only
Description   Allows authors to position a masking image in a manner
    identical to the positioning of background images. The
    default will place the masking image in the top-left
    corner of the box defined by maskorigin.
<p><b>Examples</b></p>
<pre>
p:nth-child(1) {mask-position: top right;}
p:nth-child(2) {mask-position: 33% 80%;} p:nth-child(3)
{mask-position: 5em 120%;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!-- <h3>mask-repeat Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>mask-repeat</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values    &lbrack; repeat-x &vert; repeat-y &vert; &lbrack; repeat &vert; space &vert;    
 round &vert; no-repeat &rbrack;{1,2} &rbrack;# 
Initial     repeat 
value      
Computed    As declared 
value
Applies     All elements (in SVG, applies to all graphics  
to  elements and all container elements except the defs 
        element)    
      Allows authors to repeat a masking image in a  
Description  manner identical to the repetition of background    
 images. Note that the default is to repeat a mask   
 in all directions.  
<p><b>Examples</b></p>
<pre>
p:nth-child(1) {mask-repeat: repeat;}  
p:nth-child(2) {mask-repeat: repeat round;} 
p:nth-child(3) {mask-repeat: space no-repeat;} 
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>mask-size Inh. N Anim. P</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>mask-size</h3></th>
	  <th align="right"><h3>Inh. N Anim. P</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values &lbrack; &lbrack; *&lt;length&gt;* &vert; *&lt;percentage&gt;* &vert; auto 
 &rbrack;{1,2} &vert; cover &vert; contain &rbrack;#     
Initial  auto
 value     
Computed As declared, with length values converted to
 value absolute lengths    
Applies to  All elements (in SVG, applies to all graphics  
 elements and all container elements except the defs 
 element)    
Animatable  *&lt;length&gt;* and *&lt;percentage&gt;* values only  
 *  Sets the size of the initial masking image in a     
 *Description  manner identical to the sizing of background
 images.     
<p><b>Examples</b></p>
<pre>
p:nth-child(1) {mask-size: 80%;}    
p:nth-child(2) {mask-size: 2em 3em, 100%;} p:nth-child(3) {mask-size:
cover, 100%, contain;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>mask-type  Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>mask-type</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values luminance &vert; alpha
Initial value luminance
Computed value As declared
Applies to SVG mask elements
Description Sets the blending mode when the masking image is defined
by an SVG mask element as opposed to, say, a PNG file or an entire SVG.
Of interest because most masking images use the alpha blending mode, but
mask element masks default to luminance.

<p><b>Example</b></p>
<pre>
svg #mask {mask-type: alpha;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>max-height Inh. N Anim. P</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>max-height</h3></th>
	  <th align="right"><h3>Inh. N Anim. P</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td><i>&lt;length&gt;</i> &vert; <i>&lt;percentage&gt;</i> &vert; none</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>none</td>
	</tr>
    <tr>
	  <td><b>Computed value</b></td>
	  <td>For percentages, as declared; for length values, value the absolute 
	  length; otherwise, none Refer to the height of the containing block 
	  <i>Percentages</i> </td>
	</tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements except nonreplaced inline elements and table elements  *Defines a maximum 
	  constraint on the height of the element (the exact nature of that height is dependent on 
	  the value of box-sizing). Thus, the element can be shorter than the declared value but not 
	  taller.</td>
	</tr>
    <tr>
	  <td><b>Admintable</b></td>
	  <td>Negative values are not permitted.</td>
	</tr>
<pre>
div#footer {max-height: 3em;}  
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>max-width Inh. N Anim. P</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>max-width</h3></th>
	  <th align="right"><h3>Inh. N Anim. P</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values    *&lt;length&gt;* &vert; *&lt;percentage&gt; &vert; none    
Initial   
 value none
Computed For percentages, as declared; for length values,    
 value the absolute length; otherwise, none
   Refer to the height of the containing block 
 Percentages 
Applies to  All elements except nonreplaced inline elements and 
 table elements 
Animatable  *&lt;length&gt;* and *&lt;percentage&gt;* values only  
   Defines a maximum constraint on the width of the    
 Description  element (the exact nature of that width is  
 dependent on the value of box-sizing). Thus, the    
 element can 

be narrower than the declared value but not wider. Negative values are
not permitted.

<p><b>Example</b></p>
<pre>
#sidebar img {width: 50px; max-width: 100%;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>min-height Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>min-height</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values    *&lt;length&gt;* &vert; *&lt;percentage&gt;*    
Initial     0   
value   
Computed    For percentages, as declared; for length values,    
value  the absolute length 
     Refer to the width of the containing block  
Percentages 
Applies     All elements except nonreplaced inline elements and 
to  table elements 
      Defines a minimum constraint on the height of the   
Description  element (the exact nature of that height is 
 dependent on the value of box-sizing). Thus, the    
 element can be taller than the declared value, but  
 not shorter.
     
Negative values are not permitted.  
<p><b>Example</b></p>
<pre>
div#footer {min-height: 1em;}  
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>min-width Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>min-width</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values *&lt;length&gt;* &vert; *&lt;percentage&gt;*

Initial value 0

Computed value For percentages, as declared; for length values, the
     absolute length
  Percentages   Refer to the width of the containing block

  Applies to    All elements except nonreplaced inline elements and
    table elements

  Description   Defines a minimum constraint on the width of the
    element (the exact nature of that width is dependent
    on the value of box-sizing). Thus, the element can

be wider than the declared value, but not narrower. Negative values
are not permitted.

<p><b>Example</b></p>
<pre>
div.aside {width: 13em; max-width: 33%;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>mix-blend-mode Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>mix-blend-mode</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values   normal &vert; multiply &vert; screen &vert; overlay &vert; darken &vert; 
lighten &vert; color-dodge &vert; color-burn &vert; hard-light   
&vert; soft-light &vert; difference &vert; exclusion &vert; hue &vert;   
saturation &vert; color &vert; luminosity    
Initial    normal  
 value   
Computed   As declared  
 value   
Applies    All elements 
 to 
   Changes how an element is composited with its
 Description  backdrop. The "backdrop" consists of any ancestor    
backgrounds and other elements that are "behind" the 
element being styled. The default of normal imposes  
simple alpha blending, as CSS has permitted since    
its inception. The others cause the element and its  
backdrop to be combined in various ways; for 
example, lighten means that the final result will    
show, at each pixel, either the element or its  
backdrop, whichever is lighter. darken is the same,  
except the darker of the two pixels will be shown.   
The results of these are likely to be familiar to    
users of Photoshop or any other graphic-editing 
tool.
<p><b>Examples</b></p>
<pre>
li.shadowed {mix-blend-mode: darken;} aside  
{mix-blend-mode:     
color-burn, luminosity, darken;}     
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>object-fit  Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>object-fit</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
object-fit  
Values   fill &vert; contain &vert; cover &vert; scale-down &vert; none  
Initial    fill 
 value   
Computed   As declared  
 value   
Applies    Replaced elements    
 to 
   Alters the way an image's contents are sized with    
Description  respect to its content box. The default, fill,  
causes the image to be stretched or squashed to fit  
its height and width, as images always have. none    
means the image keeps its intrinsic height and  
width, regardless of the values of the img element's 
height and width properties. contain will cause the  
entire image to be visible within its element box,   
scaled up or down as necessary, while maintaining    
its intrinsic aspect ratio. cover scales the image   
up or down to fill the image box of the image, again 
maintaining its intrinsic aspect ratio. scale-down   
means the image will stay its intrinsic size unless  
it's too big to fit into the element box, in which   
case it will be scaled down to fit.  
<p><b>Examples</b></p>
<pre>
img:nth-of-type(1) {object-fit: none;}  
img:nth-of-type(2) {object-fit: fill;}  
img:nth-of-type(3) {object-fit: cover;} 
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>object-position Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>object-position</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values *&lt;position&gt;*
Initial value 50% 50%
Computed value As declared
Applies to Replaced elements
Description Provides a way to change the position of a fitted image
(see object-fit) within its element box, in a manner identical to how
background origin images can be positioned.

<p><b>Examples</b></p>
<pre>
img:nth-of-type(1) {object-position: center;}

img:nth-of-type(2) {object-position: 67% 100%;} img:nth-of-type(3)
{object-position: left 142%;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>opacity  Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>opacity</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values    <i>&lt;number&gt;</i>
Initial     1   
value   
Computed    As declared 
value   
Applies     All elements
to 
Computed    Same as declared (or a clipped value if declared    
value  value must be clipped)
     Defines an element's degree of opacity using a 
Description  number in the range 0--1, inclusive. Any values     
outside that range are clipped to the nearest edge  
(0 or 1). This property affects every visible  
portion of an element. If it is necessary to have   
the content of an element semiopaque but not the    
background, or vice versa, use alpha color types    
such as rgba().     
     
An element with opacity of 0 is effectively 
invisible and may not respond to mouse or other DOM 
events. Because of the way semiopaque elements are  
expected to be drawn, an element with opacity less  
than 1 creates its own stacking context even if it  
is not positioned. For similar reasons, an  
absolutely positioned element with opacity less     
than 1 and a z-index of auto force-alters the  
z-index value to 0. 
<p><b>Examples</b></p>
<pre>
h2 {opacity: 0.8;} .hideme {opacity: 0;}    
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>order     Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>order</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values *&lt;integer&gt;*
Initial value 0
Computed value As declared
Applies to Flex and grid items, and the absolutely positioned
children of flex and grid containers
Description Sets a visual rendering order independently of the
document source order. One example is turning a set of list items into
flex items, and then designating a list item (or group of list items)
from the middle of the list to be the first flex items displayed in the
flex container. Because only the visual order is changed, not the DOM
order, structural selectors like :first-child will match the first
element in the source, not the first element on screen. Originally
conceived as a way to change the visual layout order of flex items, this
property now also allows authors to rearrange the order of auto-flowed
grid items.

<p><b>Examples</b></p>
<pre>
li:nth-of-type(6) {order: 1;}
li:nth-of-type(14) {order: -1;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>orphans   Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>orphans</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values    <i>&lt;integer&gt;</i>
Initial     2   
value   
Computed    As declared 
value   
Applies     Block-level elements
to 
     Defines the minimum number of text lines within an  
Description  element that can be left at the bottom of a page.   
This can affect the placement of page breaks within 
the element.
<p><b>Examples</b></p>
<pre>
p {orphans: 4;} ul {orphans: 2;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>outline   Inh. N Anim. P</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>outline</h3></th>
	  <th align="right"><h3>Inh. N Anim. P</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values &lbrack; *&lt;outline-color&gt;* ‖ *&lt;outline-style&gt;* ‖
*&lt;outlinewidth&gt;* &rbrack;
Initial value none
Computed value As declared
Applies to All elements
Animatable Outline width and color; not style
Description This is a shorthand property that defines the overall
outline for an element. The most common use of outlines is to indicate
which form element or hyperlink currently has focus (accepts keyboard
input). Outlines can be of irregular shape, and no matter how thick,
they do not change or otherwise affect the placement of elements.

<p><b>Examples</b></p>
<pre>
&ast;&lbrack;href&rbrack;:focus {outline: 2px dashed invert;}
form:focus {outline: outset cyan 0.25em;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>outline-color Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>outline-color</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values *&lt;color&gt;* &vert; invert
Initial value invert Computed value As declared
Applies to All elements
Description Defines the color for the visible portions of the
overall outline of an element. Remember that the value of outline-style
must be something other than none for any visible border to appear. User
agents are permitted to ignore invert on platforms that don't support
color inversion. In that case, the outline's color defaults to the value
of color for the element.

<p><b>Examples</b></p>
<pre>
&ast;&lbrack;href&rbrack;:focus {outline-color: invert;}
form:focus {outline-color: cyan;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>outline-offset Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>outline-offset</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>*&lt;length&gt;*</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>0</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>An absolute length value</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the offset distance between the outer border edge and inner outline edge. Only one 
	  length value can be supplied, and it applies equally to all sides of the outline. Values can 
	  be negative, which causes the outline to "shrink" inward toward the element's center. Note that 
	  outline-offset cannot be set via the shorthand outline.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
&ast;&lbrack;href&rbrack;:focus {outline-offset: 0.33em;}
form:focus {outline-offset: −1px;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>outline-style Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>outline-style</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>auto &vert; none &vert; solid &vert; dotted &vert; dashed &vert; double &vert; groove &vert; 
	  ridge &vert; inset &vert; outset</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>none</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the style for the overall border of an element. The style must be something other 
	  than none for any outline to appear.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
&ast;&lbrack;href&rbrack;:focus {outline-style: dashed;}
form:focus {outline-style: outset;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>outline-width Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>outline-width</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>&lt;length&gt;* &vert; thin &vert; medium &vert; thick</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>medium</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>absolute length, or 0 if the style of the outline value is none; otherwise, as declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the width for the overall outline of an element. The width will take effect for a 
	  given outline only if the value of outline-style is something other than none. If the style 
	  <i>is</i> none, the width is effectively reset to 0. Negative length values are not permitted.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
&ast;&lbrack;href&rbrack;:focus {outline-width: 2px;} 
form:focus {outline-width: 0.25em;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>overflow  Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>overflow</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>visible &vert; hidden &vert; scroll &vert; auto</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>visible</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>Applies Block-level and replaced elements to</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>A shorthand property that defines what happens to content that overflows the content area 
	  of an element. For the value scroll, user agents should provide a scrolling mechanism whether 
	  or not it is actually needed; for example, scrollbars would appear even if all content can fit 
	  within the element box. If two values are supplied, the first defines the value of overflow-x 
	  and the second defines overflow-y. Otherwise, a single value defines both.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
#masthead {overflow: hidden;}
object {overflow: visible scroll;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>overflow-wrap Inh. Y Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>overflow-wrap</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>normal &vert; break-word <b>Initial value</b> normal</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Allows authors to specify whether line breaks are permitted inside words that are longer 
	  than their containing element is wide and which cannot be hyphenated, either due to language 
	  or the values of other properties. If break-word is set, the linebreaking will *only* occur 
	  if the word is placed on a new text line and still cannot fit inside its element's containing 
	  block. (This behavior is in contrast to word-break, which does not force a pre-word line break.)</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
pre {overflow-wrap: break-word;}
</pre>
      </td>
	</tr>
	<tr>
	  <td><b>Note</b></td>
	  <td>This property used to be called word-wrap. Browsers that supported word-wrap in the past 
	  now use it as an alias for overflow-wrap.</td>
    </tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>overflow-x  Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>overflow-x</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>visible &vert; hidden &vert; scroll &vert; auto</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>visible</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>Block-level and replaced elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the overflow behavior along the horizontal (x) axis of the element; that is, the 
	  left and right edges of the element.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
#masthead {overflow-x: hidden;} object {overflow-x: 
visible;}   
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>overflow-y  Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>overflow-y</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>visible &vert; hidden &vert; scroll &vert; auto</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>visible</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>Block-level and replaced elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the overflow behavior along the vertical (y) axis of the element; that is, the top and bottom edges of the element.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>

<pre>
#masthead {overflow-y: hidden;} object {overflow-y:
scroll;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>padding   Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>padding</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>&lbrack; *&lt;length&gt;* &vert; *&lt;percentage&gt;* &rbrack;{1,4}</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>Not defined for shorthand elements</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>See individual properties (padding-top, etc.) </td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>A shorthand property that defines the width of the overall padding for an element or 
	  sets the widths of each individual side's padding. Padding set on inline nonreplaced elements 
	  does not affect line-height calculations; therefore, such an element with both padding and a 
	  background may visibly extend into other lines and potentially overlap other content. The 
	  background of the element will extend throughout the padding. Negative padding values are not 
	  permitted.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
img {padding: 10px;} h1 {padding: 2ex 0.33em;} 
pre {padding: 0.75em 0.5em 1em 0.5em;} 
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>padding-bottom Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>padding-bottom</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td><i>&lt;length&gt;</i> &vert; <i>&lt;percentage&gt;</i></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>0</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>For percentage values, as declared; for length values, the absolute length</td>
    </tr>
	<tr>
	  <td><b>Percentage</b></td>
	  <td>Refer to the width of the containing block</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the width of the bottom padding for an element. Bottom padding set on inline nonreplaced elements does not affect line-height calculations; therefore, such an element with both bottom padding and a background may visibly extend into other lines and potentially overlap other content. Negative padding values are not permitted.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
ul {padding-bottom: 0.5in;}
h1 {padding-bottom: 2%;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>padding-left Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>padding-left</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>&lt;length&gt;* &vert; *&lt;percentage&gt;*</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>0</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>For percentage values, as declared; for length values, the absolute length.</td>
    </tr>
	<tr>
	  <td><b>Percentages</b></td>
	  <td>Refer to the width of the containing block</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the width of the left padding for an element. Left padding set for an inline 
	  nonreplaced element will appear only on the left edge of the first inline box generated 
	  by the element. Negative padding values are not permitted.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
p {padding-left: 5%;}
pre {padding-left: 3em;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>padding-right Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>padding-right</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>*&lt;length&gt;* &vert; *&lt;percentage&gt;*</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>0</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>For percentage values, as declared; for length values,
     the absolute length</td>
    </tr>
	<tr>
	  <td><b>Percentage</b></td>
	  <td>Refer to the width of the containing block</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the width of the right padding for an element. Right padding set for an inline 
	  nonreplaced element will appear only on the right edge of the last inline box generated by 
	  the element. Negative padding values are not permitted.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
img {padding-right: 30px;}
ol {padding-right: 5em;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>padding-top Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>padding-top</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>*&lt;length&gt;* &vert; *&lt;percentage&gt;* </td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>0</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>For percentage values, as declared; for length 
   values, the absolute length 
      Refer to the width of the containing block  
 Percentages </td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the width of the top padding for an element. Top padding set on inline nonreplaced 
	  elements does not affect line-height calculations; therefore, such an element with both top 
	  padding and a background may visibly extend into other lines and potentially overlap other 
	  content. Negative padding values are not permitted.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
ul {padding-top: 0.5in;} h3 {padding-top: 1.5em;}   
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>page    Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>page</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>*&lt;identifier&gt;* &vert; auto</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>auto</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>Block-level elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the page type that *should* be used when displaying the element. The emphasis of 
	  the word "should" is taken directly from the specification, so author beware. The intended 
	  effect is that if an element has a value of page that is different than that of the preceding 
	  element, at least one page break is inserted before the element and a new page started using 
	  the page type declared by page. (Multiple page breaks may be used if other styles call for using 
	  a right- or lefthand page when starting the new page.)</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
&#64;page wide {size: landscape;}
table.summary {page: wide;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>page-break-after  Inh. N Anim.</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>page-break-after</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values    auto &vert; always     
Initial     auto  
 value  
 Computed    As declared
 value  
 Applies     Nonfloated block-level elements    
 to  with a position value of relative  
 or static  
      Defines whether one or more page   
 Description  breaks should be placed after an   
 element. Although it is    
 theoretically possible to force    
 breaks with always, it is not 
 possible to guarantee prevention;  
 avoid asks the user agent to avoid 
 inserting a page break if  
 possible. The keyword left is used 
 to insert enough breaks after the  
 element to make the next page be a 
 lefthand page; similarly, right is 
 used for a righthand page. 
<p><b>Examples</b></p>
<pre>
section {page-break-after: 
always;}
h1 {page-break-after:
avoid;}    
</pre>
Note This property is essentially  
replaced by breakafter, but
browser support for
page-break-after may be stronger.  
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>page-break-before Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>page-break-before</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values auto &vert; always
Initial value auto
Computed value As declared
Applies to Nonfloated block-level elements with a position value of
relative or static
Description Defines whether one or more page breaks should be placed
before an element. It's theoretically possible to use always to force a
page break, but while avoid asks the user agent to avoid inserting a
page break if possible, there's no guarantee it won't insert one anyway.
The keyword left is used to insert enough breaks before the element to
make the page be a lefthand page; similarly, right is used for a
righthand page.

<p><b>Examples</b></p>
<pre>
section {page-break-before: always;} h2 {page-break-before:
avoid;}
</pre>

Note This property is essentially replaced by break-
before, but browser support for page-breakbefore may be stronger.
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>page-break-inside  Inh. Y Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>page-break-inside</h3></th>
	  <th align="right"><h3>Inh. Y Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values  auto &vert; avoid   
 Initialauto    
 value  
 Computed  As declared     
 value  
 Applies to   Nonfloated block-level elements 
    with a position value of
    relative or static 
 Description  Defines whether a page break    
    should be avoided within the    
    element. Note that such 
    avoidance may not be possible;  
    for example, declaring body     
    {pagebreak-inside: avoid;} for a
    lengthy document will not  
    prevent the insertion of page   
    breaks by the user agent.  
<p><b>Example</b></p>
<pre>
table {page-break-inside:  
  avoid;} 
</pre>
Note This property is essentially    
    replaced by breakbefore, but    
    browser support for     
    page-breakbefore may be 
    stronger.  
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>perspective  Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>prespective</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values  none &vert; *&lt;length&gt;*  
Initial value none
Computed value The absolute length, or else none
Applies to Any transformable element
Description Defines the amount of apparent 3D perspective of an
element's transformed children, but not for the element itself. Numbers
define a foreshortening depth in pixels; smaller numbers define more
extreme perspective effects. Negative values are treated the same as
none.

<p><b>Examples</b></p>
<pre>
body {perspective: 250;} /&ast; middlin&apos; &ast;/
#wrapper {perspective: 10;} /&ast; extreme &ast;/
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>perspective-origin Inh. N Anim. P</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>perspective-origin</h3></th>
	  <th align="right"><h3>Inh. N Anim. P</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values    <i>&lt;position&gt;</i> 
Initial     50% 50%     
value      
Computed    A percentage, except for length values, which are   
value  converted to an absolute length     
     Refer to the size of the bounding box  
Percentages 
Applies     Any transformable element   
to 
  *&lt;length&gt;* and *&lt;percentage&gt;* values only  
Animatable 
     Defines the origin point of the apparent 3D 
Description  perspective within the element. In effect, it  
defines the point in the element that appears to be 
directly in front of the viewer.    
<p><b>Examples</b></p>
<pre>
body {perspective-origin: bottom right;} #wrapper   
div {perspective-origin: 0 50%;}    
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>position Inh. N Anim. N</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>position</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values static &vert; relative &vert; sticky &vert; absolute &vert; fixed
Initial value static Computed value As declared
Applies to All elements
Description Defines the positioning scheme used to lay out an
element. Any element may be positioned, although an element positioned
with absolute or fixed will generate a block-level box regardless of
what kind of element it is. An element that is relatively positioned is
offset from its default placement in the normal flow.

<p><b>Examples</b></p>
<pre>
#footer {position: fixed; bottom: 0;}
&ast;.offset {position: relative; top: 0.5em;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>quotes   Inh. Y Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>quotes</h3></th>
	  <th align="right"><h3>Inh. Y Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values    &lbrack; *&lt;string&gt;* *&lt;string&gt;* &rbrack;+ &vert; none    
Initial     User agent--dependent  
value      
Computed    As declared 
value      
Applies     All elements
to 
     Defines the quotation pattern used with quotes and  
Description  nested quotes. The actual quote marks are inserted  
via the content property's open-quote and   
closequote values.  
<p><b>Examples</b></p>
<pre>
q:lang(fr) {quotes: &quot;«&quot; &quot;»&quot; &quot;‹&quot; &quot;›&quot;;} q     
 {quotes: &apos;\\201C&apos; &apos;\\201D&apos; &apos;\\2018&apos;   
 &apos;\\2019&apos;;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>resize  Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>resize</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values none &vert; both &vert; horizontal &vert; vertical
Initial value none
Computed value As declared
Applies to Elements whose overflow value is not visible
Description Defines how (or whether) an element can be resized by
the user. The actual appearance and operation of any resize mechanism is
left to the user agent and is likely dependent on the writing direction.

<p><b>Examples</b></p>
<pre>
textarea {resize: vertical;} iframe {resize: both;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>right    Inh. N Anim. P</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>right</h3></th>
	  <th align="right"><h3>Inh. N Anim. P</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>

 Values    <i>&lt;length&gt;</i> &vert; <i>&lt;percentage&gt;</i> &vert; auto    
 Initial     auto
 value      
 Computed    For static elements, auto; for length values, the   
 value  corresponding absolute length; for percentage  
 values, the specified value; otherwise, auto
      Refer to the height of the containing block 
 Percentages 
 Applies     Positioned elements 
 to 
  <i>&lt;length&gt;</i> and <i>&lt;percentage&gt;</i> values only  
 Animatable 
      Defines the offset between the right outer margin   
 Description  edge of a positioned element and the right edge of  
 its containing block.  
<p><b>Examples</b></p>
<pre>
div#footer {position: fixed; right: 0;}     
&ast;.overlapper {position: relative; right: −25px;}   
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  shape-image-threshold Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>shape-image-threshold</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values   <i>&lt;number&gt;</i>
Initial    0.0  
value      
Computed   The same as the specified value after clipping the   
value *&lt;number&gt;* to the range &lbrack;0.0, 1.0&rbrack;  
Applies    Floats  
to 
   Changes the alpha channel value that acts as a  
Description  threshold for float shape creation via an image. By  
default, only fully transparent areas in the shape's 
source image are used to define the float shape. If  
<p><b>Examples</b></p>
the value is changed to 0.7, then all areas of the   
source image that are 70% or more transparent are    
used to define the float shape. This allows for the  
same image to be used to define multiple float  
shapes, for example. A value of 0 will cause the     
entire image to be ignored for shape calculation.    
<pre>
aside.illustrate {shape-image-threshold: 0.667;}     
img.floated {shape-image-threshold: 0.1;}    
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>shape-margin Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>shape-margin</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values <i>&lt;length&gt;</i> &vert; <i>&lt;percentage&gt;</i>
Initial value 0
ComputedAn absolute length
  value   
Applies to    Floats
Description   Defines an offset distance between the edges of a
    float shape and the closest points at which text may
    approach the shape. This is useful when floating an
    image and using that same image to define the float
    shape, but wanting the keep normal-flow text away from
    the visible edges of the image. Note that the float
    shape and shape margin are clipped beyond the outer
    margin edge of the original float, so excessively
    large shape margins are most likely to result in a
    traditional rectangular float box.
<p><b>Examples</b></p>
<pre>
#one {shape-margin: 0;}
#two {shape-margin: 1.5em;}
#thr (shape-margin: 10%;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>shape-outside Inh. N Anim. P</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>shape-outside</h3></th>
	  <th align="right"><h3>Inh. N Anim. P</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values   none &vert; &lbrack; <i>&lt;basic-shape&gt;</i> ‖ <i>&lt;shape-box&gt;</i> &rbrack; &vert; 
   &lt;image&gt;
  inset &vert; circle() &vert; ellipse() &vert; polygon()  
Definitions  
      
&lt;bas     
 ic-shape&gt;
 &lt;s  margin-box &vert; border-box &vert; padding-box &vert;   
 hape-box&gt;  contentbox   
 Initial    none 
 value      
 Computed value  For a <i>&lt;basic-shape&gt;</i>, as defined for an   
 <i>&lt;image&gt;</i>, its URI made absolute; otherwise, as    
   declared     
 Applies    Floats  
 to 
     <i>&lt;basic-shape&gt;</i> values only
 Animatable  
 Description  Defines the shape of a floated element for the  
 purposes of calculating text flow past the float.    
   Possibilities include defining a polygon that echoes 
   the outer    

edge of an illustration, or using that image's transparent areas to
define the float shape. Shapes are clipped at the edges of the shape's
outer margin edge, so a float shape can never be larger than the
unshaped version of that float.

<p><b>Examples</b></p>
<pre>
img.web20 {shape-outside: inset(7% round 0.5em/5px);}
img.curio {shape-outside: circle(25px at 50% 50%);} aside.diamond
{shape-outside: polygon(50% 0, 100% 50%, 50% 100%, 0 50%);}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>size     Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>size/h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>auto &vert; <i>&lt;length&gt;</i>{1,2} &vert; &lbrack; <i>&lt;page-size&gt;</i> 
	  &vert;&vert; &lbrack; portrait &vert; landscape &rbrack; &rbrack;</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>auto</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td><i>&lt;length&gt;</i> values as absolute length values; otherwise, as declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>The page area </td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the size and orientation of a page box. The keywords auto, portrait, and 
	  landscape cause the page box to fill the available rendering space on the page. Page 
	  boxes set to portrait have the content printed with the long sides of the page box 
	  being the right and left sides; in the case of landscape, the content is printed with 
	  the longer sides of the page box being the top and bottom sides. If a page box is 
	  specified using lengths or one of the *&lt;page-size&gt;</i> keywords (e.g., A4) and 
	  the page box cannot be fit onto the actual page used for display, the page box and 
	  its contents may be scaled down to fit. If only one length value is declared, it sets 
	  both dimensions and thus defines a square page box. Length values that use em or ex 
	  units are calculated with respect to the computed font size of the page context.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
body   
{page-size:    
landscape;}    
</pre>
      </td>
	</tr>
	<tr>
	  <td><b>Note</b></td>
	  <td>*&lt;page-size&gt;</i> is one of a defined set of standard page sizes; see Chapter 20 of [*CSS: The</i> *Definitive Guide</i>, 4th Edition](http://shop.oreilly.com/product/0636920012726.do), for details.</td>
    </tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!-- <h3>tab-size  Inh. Y Anim. Y</h3> -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>tab-size</h3></th>
	  <th align="right"><h3>Inh. Y Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td><i>&lt;length&gt;</i> &vert; <i>&lt;integer&gt;</i></td>
	</tr>
    <tr>
	  <td><b>Initial values</b></td>
	  <td>8</td>
	</tr>
    <tr>
	  <td><b>Computed values</b></td>
	  <td>The absolute-length equivalent of the value</td>
	</tr>
    <tr>
	  <td><b>Applies to</b></td>
	  <td>block elements</td>
	</tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Sets the width of tab characters' whitespace when they are present in the displayed 
	  source <i>and</i> are honored for display due to the value of whitespace. An <i>&lt;integer&gt;</i> 
	  value sets the number of "spaces" a tab character will generate.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
pre.source {tab-size: 4;}   
p.typer {tab-size: 0.25in;} 
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<h3>table-layout Inh. Y Anim. N</h3>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>table-layout</h3></th>
	  <th align="right"><h3>Inh. Y Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>auto &vert; fixed</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>auto</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>Elements with the display value table or inlinetable</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines whether a table element should be laid out using an automatic-layout algorithm 
	  or a fixedlayout algorithm. The benefit of the automatic algorithm is that it's very similar 
	  to what authors are used to from more than a decade of browser behavior. However, the fixed-layout 
	  algorithm is theoretically faster and more predictable.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
table.data {table-display: fixed;}
table.directory {table-display: auto;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>text-align Inh. Y Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>text-align</h3></th>
	  <th align="right"><h3>Inh. Y Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>start &vert; end &vert; left &vert; right &vert; center &vert; justify &vert; match-parent &vert; start end</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>In CSS3, start; in CSS2.1, this was user agent--specific, likely depending on writing 
	  direction (e.g., left for Western languages like English)</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared, except in the case of match-parent</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>Block-level elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the horizontal alignment of text within a block-level element by defining the point 
	  to which line boxes are aligned. The value justify is supported by allowing user agents to 
	  programmatically adjust the word (but not letter) spacing of the line's content; results may 
	  vary by user agent.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
p {text-align: justify;} h4 {text-align: center;}   
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>text-align-last   Inh. Y Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>text-align-last</h3></th>
	  <th align="right"><h3>Inh. Y Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>auto &vert; start &vert; end &vert; left &vert; right &vert; center &vert; justify</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>auto</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>Block-level elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the horizontal alignment of the last line of text within a block-level element by 
	  defining the point to which line boxes are aligned. The value justify is supported by allowing 
	  user agents to programmatically adjust the word (but not letter) spacing of the line's content; 
	  results may vary by user agent.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
p {text-align-last: justify;}
h4 {text-align-last: right;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>text-decoration Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>text-decoration</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>none &vert; &lbrack; underline ‖ overline ‖ line-through ‖ blink &rbrack;</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>none</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines text-decoration effects such as underlining. These decorations will span descendant 
	  elements that don't have decorations of their own, in many cases making the child elements 
	  appear to be decorated. Combinations of the values are legal. Any time two text-decoration 
	  declarations apply to the same element, the values of the two declarations are <i>not</i> combined.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
h1 {text-decoration: overline;} h1, h2
{text-decoration: underline;}
</pre>
      </td>
	</tr>
  </tbody>
</table>

<!--
Given these styles, h1 elements will be underlined  
with no overline because the value of underline     
completely overrides the value of overline. If h1   
should have both overlines and underlines, use the  
value overline underline for the h1 rule and either 
move it after the h1, h2 rule or extend its 
selector to raise its specificity.  
     
User agents are not required to support blink. 
<p><b>Examples</b></p>
<pre>
u {text-decoration: underline;}     
.old {text-decoration: line-through;}  
u.old {text-decoration: line-through underline;}    
</pre>
-->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>text-indent  Inh. Y Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>text-indent</h3></th>
	  <th align="right"><h3>Inh. Y Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td><i>&lt;length&gt;</i> &vert; <i>&lt;percentage&gt;</i></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>0</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>For percentage values, as declared; for length
values, the absolute length</td>
    </tr>
	<tr>
	  <td><b>Percentages</b></td>
	  <td>Refer to the width of the containing block</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>Block-level elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the indentation of the first line of content in a block-level element. This property is most often used to create a tab effect. Negative values are permitted and cause outdent (or hanging indent) effects. In CSS3, the value each-line will apply the indentation to any new line that results from a forced line break (e.g., due to a br element) within the element, not just the first line. The value hanging inverts the defined pattern of indentation, allowing for the creation of an outdent effect without using a negative length value.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
p {text-indent: 5em;}
h2 {text-indent: −25px;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>text-orientation Inh. Y Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>text-orientation</h3></th>
	  <th align="right"><h3>Inh. Y Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>mixed &vert; upright &vert; sideways</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>mixed</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements except table row groups, table rows, table column groups, and table columns</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines how characters are oriented in text, potentially independent of their writing mode (see writing-mode). When mixed, each character is aligned according to its language defaults as compared to the writing direction; for example, mixed English and Japanese text written in a vertical writing mode would have the English characters sideways and the Japanese characters upright. upright forces all characters to be upright regardless of their language, and sideways forces all characters to be shown sideways.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
#one {text-orientation: mixed;}
### two {text-orientation: upright;}
### thr {text-orientation: sideways;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>text-rendering Inh. Y Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>text-rendering</h3></th>
	  <th align="right"><h3>Inh. Y Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>auto &vert; optimizeSpeed &vert; optimizeLegibility &vert; geometricPrecision</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>auto</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Sets the approach used to render text, allowing
authors to decide if speed, legibility, or precision is most
important. Note that some user agents always optimize for legibility
when rendering HTML text, so this property may have minimal or no
effect outside of SVG (which is where it started out)..</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
p {text-rendering: optimizeSpeed;}
svg tspan {text-rendering: optimizeLegibility;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>text-shadow Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>text-shadow</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>none &vert; &lbrack;<i>&lt;length&gt;</i> ‖ <i>&lt;color&gt;</i>? &&
    <i>&lt;length&gt;</i>{2,3}&rbrack;#</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>none</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>color plus three absolute lengths</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines one or more shadows to be "cast" by the text
    of an element. Shadows are always painted behind the
    element's text, but in front of the element's
    background, borders, and outline. Shadows are drawn
    from the first on top to the last on the bottom. The
    three length values that can be declared are, in

order: horizontal offset, vertical offset, and blur distance. When
positive, the offset values go down and to the right; when negative,
they go back and to the left. Blur values cannot be negative..</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
h1 {text-shadow: 0.5em 0.33em 4px gray;} h2 {text-shadow: 0
−3px 0.5em blue;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>text-transform Inh. Y Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>text-transform</h3></th>
	  <th align="right"><h3>Inh. Y Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
Values    uppercase &vert; lowercase &vert; capitalize &vert; none
Initial value    none
Computed value   As declared 
Applies to    All elements
Description:     Defines the pattern for changing the case of
 letters in an element, regardless of the case of    
 the text in the document source. The determination  
 of which letters are to be capitalized by the value 
 capitalize is not precisely defined, as it depends  
 on user agents knowing how to recognize a "word."   
<p><b>Examples</b></p>
<pre>
h1 {text-transform: uppercase;} .title
{text-transform: capitalize;}
</pre>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>top Inh. N Anim. P</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>top</h3></th>
	  <th align="right"><h3>Inh. N Anim. P</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td><i>&lt;length&gt;</i> &vert; <i>&lt;percentage&gt;</i> &vert; auto</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>auto</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>For static elements, auto; for length values, the 
 corresponding absolute length; for percentage
 values, the specified value; otherwise, auto
   Refer to the height of the containing block</td>
    </tr>
	<tr>
	  <td><b>Percentage</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>Positioned elements </td>
    </tr>
	<tr>
	  <td><b>Animatable</b></td>
	  <td><i>&lt;length&gt;</i> and <i>&lt;percentage&gt;</i> values only  
   Defines the offset between the top outer margin .</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>edge of a positioned element and the top edge of its containing block.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
#masthead {position: fixed; top: 0;} sub {position: 
relative; top: 0.5em; vertical-align: baseline;}    
</pre>
      </td>
	</tr>
	<tr>
	  <td><b>Note</b></td>
	  <td>For relatively positioned elements, if both top and bottom are auto, their computed values are both 0. If one of them is auto, it becomes the negative of the other; if neither is auto, bottom becomes the negative of the value of top.</td>
    </tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>transform   Inh. N Anim. P</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>transform</h3></th>
	  <th align="right"><h3>Inh. N Anim. P</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td><i>&lt;transform-list&gt;</i> &vert; none</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>none</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared, except for relative length values, which are converted to an absolute length. Refer to the size of the bounding box.</td>
    </tr>
	<tr>
	  <td><b>Percentages</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements except "atomic inline-level" boxes. As a transform.</td>
    </tr>
	<tr>
	  <td><b>Animatable</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines one or more transforms of an element. These transforms can occur in a 2D or a 
	  simulated 3D space, depending on how the transforms are declared. The permitted values for 
	  <i>&lt;transform-function&gt;</i> are lengthy and complex. For a full list with minimalist 
	  descriptions, please consult the W3C's documentation on 
	  <a href="http://w3.org/TR/css3-3d-transforms/#transform-functions">transform functions</a>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
table th {transform: rotate(45deg);} li {transform: 
scale3d(1.2,1.7,0.85);}     
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>transform-origin   Inh. N Anim. P</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>transform-origin</h3></th>
	  <th align="right"><h3>Inh. N Anim. P</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td><i>&lt;position&gt;</i></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>50% 50%</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>A percentage, except for length values, which are converted to an absolute length. Refer to the size of the bounding box.</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>Any transformable element <i>&lt;length&gt;</i> and <i>&lt;percentage&gt;</i> values only</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>in either 2D or simulated 3D space. The marked-as-optional <i>&lt;length&gt;</i> values are what define a 3D origin point; without them, the value is necessarily in 2D space.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
table th {transform-origin: bottom left;}
li {transform-origin: 10% 10px 10em;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>transform-style Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>transform-style</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>flat &vert; preserve-3d</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>flat</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>Any transformable element. Defines whether an element transformed in simulated.</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>3D space should have its children rendered using a flat style, thus putting them all in the same 2D plane as the element, or attempt to use a 3D effect where children with positive or negative zindex values may be rendered "in front of" or "behind" the element's plane as it rotates. Elements whose overflow value is hidden cannot preserve 3D effects and are treated as though the value of transform-style is flat.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
li {transform-style: preserve-3d;}  
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>transition  Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>transition</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>&lbrack; &lbrack; none &vert; <i>&lt;transition-property&gt;</i> &rbrack; ‖
 <i>&lt;time&gt;</i> ‖ <i>&lt;transition-timing-function&gt;</i> ‖  <i>&lt;time&gt;</i> &rbrack;#</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>all 0s ease 0s</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared </td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements and :before and :after pseudoelements A shorthand property that defines the aspects of.</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>One or more of an element's transitions from one state to another. Even though it is not (as of 
	  this writing) explicitly defined in the value syntax, descriptive text in the specification defines 
	  that when two <i>&lt;time&gt;</i> values are declared, the first is the duration and the second is the 
	  delay. If only one is declared, it defines only the duration.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
a:hover {transition: color 1s 0.25s ease-in-out;} h1
{transition: linear all 10s;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>transition-delay Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>transition-delay</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td><i>&lt;time&gt;</i>&#35;</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>0s</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements and :before and :after pseudoelements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines a delay between when a transition could theoretically first start and when it actually starts. For example, if a transition is defined to begin on hover but has a delay of 0.5s, the transition will actually begin half a second after the element is first hovered over. Negative time values are permitted, but rather than creating a paradox, this simply jumps the transition to the point it would have reached had it been started at the defined time offset in the past. In other words, it will be started partway through the transition and run to its conclusion.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
a&lbrack;href&rbrack;:hover {transition-delay: 0.25;}
h1 {transition-delay: 0;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>transition-duration Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>transitions-duration</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td><i>&lt;time&gt;</i>&#35;</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>0s</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements and :before and :after pseudoelements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the length of time it takes for the transition to run from start to finish. The default 0s means the transition is instantaneous and no animation occurs. Negative time values are treated as 0s.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
a&lbrack;href&rbrack;:hover {transition-duration: 1s;}
h1 {transition-duration: 10s;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>transition-property Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>transition-property</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>none &vert; &lbrack; all &vert; <i>&lt;property-name&gt;</i> &rbrack;#</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>All</td>
	</tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
	</tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements and :before and :after pseudoelements</td>
	</tr>
	<tr>
	  <td><b>Animatable</b></td>
	  <td>Refer to individual border-image properties to see which are animatable.</td>
	</tr>
	  <td><b>Description</b></td>
	  <td>Defines one or more properties that are transitioned from one state to another; for 
	  example, color means that the foreground color of an element is transitioned from the start 
	  color to the finish color. If a shorthand property is declared, the transition parameters 
	  meant for that property are propagated to all the properties represented by the  shorthand. 
	  The keyword all means all properties are transitioned. The keyword none prevents any properties 
	  from being transitioned, effectively shutting down the transition.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
a&lbrack;href&rbrack;:hover {transition-property: color;}
h1 {transition-property: all;} 
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>transition-timing-function Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>transition-timing-function</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td><i>&lt;timing-function&gt;</i>&#35;</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>See individual properties</td>
	</tr>
    <tr>
	  <td><b>Definition</b></td>
	  <td><b><i>&lt;timing-function&gt;</i></b>ease &vert; linear &vert; ease-in &vert; 
	  ease-out &vert;ease-in-out &vert;cubic-bezier(<i>&lt;number&gt;</i>,<i>&lt;number&gt;</i>,
	  <i>&lt;number&gt;</i>,<i>&lt;number&gt;</i>)</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>ease</td>
	</tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>ComputedAs value to</b></td>
	  <td>declared</td>
	</tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements and :before and :after pseudoelements</td>
	</tr>
	  <td><b>Description</b></td>
	  <td>Defines the way in which intermediate states of a transition are calculated. The value keywords (ease, linear, etc.) are shorthands for specific cubicbezier() values defined in the specification, so in effect all values of this property are cubic-bezier() values.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
a&lbrack;href&rbrack;:hover {transition-timing-function:
ease-in-out;}
h1 {transition-timing-function: linear;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>unicode-bidi Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>  </h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>normal &vert; embed &vert; bidi-override</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>normal</td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Allows the author to generate levels of embedding within the Unicode Bidirectional Algorithm. User agents that do not support bidirectional ("bidi") text are permitted to ignore this property.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
span.name {direction: rtl; unicode-bidi: embed;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>vertical-align    Inh. N Anim. P</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>vertical-align</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>baseline &vert; sub &vert; super &vert; top &vert; text-top &vert; middle &vert;
      bottom &vert; text-bottom &vert; <i>&lt;length&gt;</i> &vert; <i>&lt;percentage&gt;</i></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>baseline</td>
	</tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>For percentage and length values, the absolute length; otherwise, as declared </td>
	</tr>
    <tr>
	  <td><b>Percentages</b></td>
	  <td>Refer to the value of line-height for the element</td>
	</tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>Inline elements and table cells</td>
	</tr>
	<tr>
	  <td><b>Animatable</b></td>
	  <td><i>&lt;length&gt;</i> and <i>&lt;percentage&gt;</i> values only.</td>
	</tr>
	  <td><b>Description</b></td>
	  <td>Defines the vertical alignment of an inline element's baseline with respect to the baseline of 
	  the line in which it resides. Negative length and percentage values are permitted, and they lower 
	  the element instead of raising it. In table cells, this property sets the alignment of the content 
	  of the cell within the cell box. When applied to table cells, only the values baseline, top, middle, 
	  and bottom are recognized.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
sup {vertical-align: super;}
.fnote {vertical-align: 50%;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>visibility Inh. Y Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>visibility</h3></th>
	  <th align="right"><h3>Inh. Y Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>visible &vert; hidden &vert; collapse</td>
	</tr>
    <tr>
	  <td><b>Initial value</b></td>
	  <td>visible</td>
	</tr>
    <tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
	</tr>
    <tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
	</tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines whether the element box generated by an element is rendered. This means 
	  authors can have the element take up the space it would ordinarily take up, while 
	  remaining completely invisible. The value collapse is used in tables to remove 
	  columns or rows from the table's layout.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
ul.submenu {visibility: hidden;} tr.hide    
{visibility: collapse;}     
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>white-space Inh. N Anim. N</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>white-space</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>normal &vert; nowrap &vert; pre &vert; pre-wrap &vert; pre-line</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>normal</td>
	</tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
	</tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
	</tr>
	<td>
	  <td><b>Description</b></td>
	  <td>Defines how whitespace within an element is handled during layout. normal acts 
	  as web browsers have traditionally treated text, in that it reduces any sequence of 
	  whitespace to a single space. pre causes whitespace to be treated as in the HTML 
	  element pre, with both whitespace and line breaks fully preserved. nowrap prevents 
	  an element from linebreaking, like the nowrap attribute for td and th elements in 
	  HTML4. The values pre-wrap and preline were added in CSS2.1; the former causes the 
	  user agent to preserve whitespace while still automatically wrapping lines of text, 
	  and the latter honors newline characters within the text while collapsing all other 
	  whitespace as per normal.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
td {white-space: nowrap;}
tt {white-space: pre;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>widows   Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>widows</h3></th>
	  <th align="right"><h3>Inh. N Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td><i>&lt;integer&gt;</i></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>2</td>
	</tr>
    <tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
	</tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>Block-level elements</td>
	</tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the minimum number of text lines within an element that can be left at 
	  the top of a page. This can affect the placement of page breaks within the element.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
p {widows: 4;} ul {widows: 2;} 
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>width    Inh. N Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>width</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td><i>&lt;length&gt;</i> &vert; <i>&lt;percentage&gt;</i> &vert; auto</td>
	</tr>
	<tr>
	  <td><b>Percentages</b></td>
	  <td>Refer to the width of the containing block</td>
	</tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>See individual properties</td>
	</tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements except nonreplaced inline elements, table rows, and row groups</td>
	</tr>
	  <td><b>Description</b></td>
	  <td>Defines the width of an element's content area, outside of which padding, borders, 
	  and margins are added. This property is ignored for inline nonreplaced elements. 
	  Negative length and percentage values are not permitted.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
table {width: 80%;}
#sidebar {width: 20%;}
.figure img {width: 200px;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>word-break  Inh. Y Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>word-break</h3></th>
	  <th align="right"><h3>Inh. Y Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>normal &vert; break-all &vert; keep-all</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>normal</td>
	</tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
	</tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
	</tr>
	<tr>
	  <td><b>Animatable</b></td>
	  <td>Refer to individual border-image properties to see which are animatable.</td>
	</tr>
	  <td><b>Description</b></td>
	  <td>Defines how text should be wrapped in situations where it would not ordinarily be 
	  wrapped; for example, a very long string of numbers containing no spaces, such as the 
	  first thousand digits of pi. The value break-all permits user agents to break a word 
	  (text string) at arbitrary points if it cannot find regular breakpoints within the word.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
td {word-break: break-all;} p {word-break: normal;} 
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>word-spacing Inh. Y Anim. Y</h3>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>word-spacing</h3></th>
	  <th align="right"><h3>Inh. Y Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td><i>&lt;length&gt;</i> &vert; normal</td>
	</tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements</td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>Defines the amount of whitespace to be inserted between words. Note that the 
	  specification does not define what constitutes a "word." In typical practice, user 
	  agents will apply this to the collapsed whitespace between strings of nonwhitespace 
	  characters. Negative length values are permitted and will cause words to bunch closer 
	  together.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
p.spacious {word-spacing: 6px;} em {word-spacing: 0.2em;}
p.cramped {word-spacing: −0.5em;}
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--  <h3>writing-mode Inh. Y Anim. Y</h4>  -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>writing-mode</h3></th>
	  <th align="right"><h3>Inh. Y Anim. Y</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td>horizontal-tb &vert; vertical-rl &vert; vertical-lr</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>horizontal-tb</td>
	</tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
	</tr>
    <tr>
	  <td><b></b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>All elements except table row groups, table column groups, table rows, table columns, 
	  Ruby base containers, and Ruby annotation containers</td>
	</tr>
	  <td><b>Description</b></td>
	  <td>Allows the author to change the writing method used to flow text and other inline content 
	  into the element. The vertical values are useful for languages that are  primarily vertical, 
	  as is the case with many non-Roman languages. It is possible to have text from a normally 
	  horizontal language (e.g., German or Hebrew) flowed  into a vertical writing mode, though the 
	  orientation of the characters may not be as expected (see text-orientation). Similarly, it's 
	  possible to take a  normally vertical language and flow it horizontally  with horizontal-tb.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
&lbrack;lang=&quot;en&quot;&rbrack; {writing-mode: horizontal-tb;} 
&lbrack;lang=&quot;jp&quot;&rbrack; {writing-mode: vertical-rl;} 
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!-- <h3>z-index</h3> -->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<table>
  <thead>
    <tr>
	  <th>z-index</th>
	  <th>Inh. N Anim. Y</th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td><i>&lt;integer&gt;</i> &vert; auto</td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>auto</td>
	</tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td>As declared</td>
	</tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td>Positioned elements</td>
	</tr>
	  <td><b>Description</b></td>
	  <td>Defines the placement of a positioned element along the z-axis, which is defined to be the axis that extends perpendicular to the display area. Positive numbers are closer to the user, and negative numbers are farther away.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td><pre>#masthead {position: relative; z-index: 10000;}</pre></td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!-- wip
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>Type Selector</h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td><br>
	     <br>
	  </td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td>See individual properties</td>
	</tr>
    <tr>
	  <td><b></b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b></b></td>
	  <td></td>
	</tr>
	  <td><b>Description</b></td>
	  <td>
	  </td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
-->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3> Name here </h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Pattern</b></td>
	  <td></td>
	</tr>
	  <td><b>Description</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3>  </h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Pattern</b></td>
	  <td>  </td>
	</tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>
-->
<!--
<table style="width:500px;">
  <thead>
    <tr>
	  <th width="200"><h3> </h3></th>
	  <th align="right"><h3>Inh. N Anim. N</h3></th>
	</tr>
  </thead>
  <tbody>
    <tr>
	  <td><b>Values</b></td>
	  <td></td>
	</tr>
	<tr>
	  <td><b>Initial value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Computed value</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Applies to</b></td>
	  <td></td>
    </tr>
	<tr>
	  <td><b>Description</b></td>
	  <td>.</td>
    </tr>
	<tr>
	  <td><b>Examples</b></td>
	  <td>
<pre>
</pre>
      </td>
	</tr>
  </tbody>
</table>

-->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
<!--~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~-->
