[W3C Open Source Software
W3C Specs Q&A Weblog Past Projects Contribute About W3C
About W3C Software
OSI Approved Open Source License
The natural complement to W3C specifications is running code. Implementation and testing is an essential part of specification development and releasing the code promotes exchange of ideas in the developer community.
All W3C software is certified Open Source/Free Software. (See the license)
b6+ version 1.154
2025-11-21 B6+, the slide framework, has some improvements, especially for accessibility:
Users of screen readers (an accessibility tool) can press the N key during a presentation to hear the comment (speaker notes) for the current slide. Press N a second time to again hear the contents of the slide itself.
Bug fix: Again for users of screen readers: When going backwards through a list of incrementally displayed elements, the current element is spoken, just as when going forward.
B6+ sets the ARIA attribute role=application, to signal to screen readers that it wants to handle keystrokes. But it is not clear if that leads to the best user interface for all screen readers, so, as an experimental feature, you can tell b6+ to not set that attribute.
Improvements to the function to toggle comments on/aff in index mode, so that the display jumps less when comments are turned on or off.
Some performance enhancements.
(News Archive)
b6+ version 1.147
2025-05-09 B6+, the slide framework, has a number of new features:
When a slide contains a video or audio, it is rewound each time the slide is displayed. And when it is set to “autoplay”, it also starts automatically.
Setting the class “textfit” on a slide causes b6+ to automatically reduce the font size on that slide if needed to make it fit on the slide. The class can also be set on the BODY element.
Similarly, the class autosize can be set on images, to let b6+ try and scale them down and avoid that a slide overflows.
If there is an external screen attached, b6+ will automatically try to use that when going into slide mode. (Not supported by all browsers.)
A button and a key press allow toggling the display of speaker notes in index mode. The notes are initally hidden, but that can be reversed with a class or a URL parameter.
(News Archive)
b6+ version 1.132
2025-02-21 B6+, the slide framework, now includes a guide for style sheet writers, to help with making new slide styles.
(News Archive)
html-xml-utils 8.7
2025-02-16 Version 8.7 of the HTML-XML-utils fixes a bug in hxnormalize that caused some lines in the output to be shorter than requested by the -l option.
(News Archive)
b6+ version 1.124
2025-02-13 B6+, the slide framework, has two new features:
B6+ supports a simple form of “slipshow” presentations: Rather than putting all topics on separate slides, you add them one by one to a long “scroll” that automatically moves earlier topics up to make room for the next one. (See an example.)
B6+ allows drawing on the slide with the mouse, e.g., to underline text or circle some items. This could replace a laser pointer and is also useful when screen-sharing in a video conference.
(News Archive)
b6+ version 1.116
2025-01-06 B6+, the slide framework, now supports automatic slide shows, where the next slide appears after a given time. They can be paused with a key press. Running continuously in a loop is also possible.
(News Archive)
News Archives: 2025, 2024, 2023, 2022, 2021, 2020, 2019, 2018, 2017, 2016, 2015, 2014, 2013, 2012, 2011, 2010, 2009, 2008, 2007, 2006, 2005, 2004, 2003.
Server-side
Apache patches
Jigsaw
Hcalproxy
Browse, Parse, View
Amaya
CWM
IsaViz
Authoring tools
Amaya
HTML Slidy
b6+
Validation, lint
Charlint
CSS Validator
Link Checker
Log Validator
mobileOK checker
Markup Validator
RDF Validator
HTML Tidy
XSV
I18n checker
WPT
Manipulation, Libraries
csvtotab/tabtocsv
DTD2Schema
eot-utils
Ical2html
HTML-XML-utils
libwww
mail-transcode
RDFPic
rdjpgxmp, wrjpgxmp, xmptool
recut
gf-markdown-awk
IRC, meeting tools
AgendaBot
scribe.perl
zakim-monitor
GHURLBot a.k.a. “gb”
Browse W3C's Open Source Software
Amaya - a Web browser/editor
First released Feb '97, Amaya is not just a browser, but a hypertext editor. It's a test-bed for the design of embedded objects, stylesheets, math, structured graphics, and more.
Apache patches
Our contributions to the Apache HTTP server cover bug patches and extensions to the HTTP perl test framework as needed. We have applied all of these patches to our production servers.
Charlint
Charlint, aka "Charlie", is a perl script that allows you to validate or normalize Unicode (UTF-8) data according to the Character Model for the World Wide Web W3C Working Draft.
CSS Validator
The W3C CSS Validation Service, also known as CSS validator, is a popular free online service to find problems in CSS style sheets used by your HTML pages. The CSS Validator is also available for download.
Cwm
Cwm is a general-purpose data processor for the semantic web. It is a forward chaining reasoner which can be used for querying, checking, transforming and filtering information. Its core language is RDF, extended to include rules, and it uses RDF/XML or N3 serializations as required.
DTD2Schema
A Conversion Tool from DTD to XML Schema
eot-utils
The eot-utils are the two programs mkeot and eotinfo. The former creates an EOT (Embedded OpenType) file from an OpenType or TrueType font and the URLs of one or more Web pages. Unlike Microsoft's WEFT, mkeot is a command-line utility. mkeot doesn't subset a font and doesn't currently compress the font data. mkeot respects the TrueType “embedding bits.” The eotinfo program displays the contents of an EOT header in a human-readable way. The programs were tested on Linux (Debian 5 “Lenny”) and Mac OS X (10.5 “Snow Leopard”) but are expected to work on more systems.
HTML Slidy
A Web-based framework for creating accessible slide shows with simple markup, and operated like Microsoft PowerPoint. Each presentation is marked up as a single document with links to the slideshow style sheet and script. Each slide is enclosed in a div element with class="slide". The framework includes support for handout notes, incrementally revealing bullet points and graphics overlays, different backgrounds for different slides (div's with class="background"), and guidance on using SVG for anti-aliased graphics that scale with the window size.
b6+
Another framework for HTML slide shows. b6+ is a script in JavaScript, which is attached to an HTML file to display the file as a series of slides. Each slide is an element (div, section or similar) with a class of slide (this format is compatible with the Shower framework), but it is also possible to just start a slide with an h1 element without wrapping the slide in an element. The slide then ends at the next h1. See the documentation (which is itself a slide show) for its other features.
HTML Tidy
HTML TIDY is a free utility for fixing HTML mistakes automatically and tidying up sloppy editing into nicely laid out markup. It also works great on the atrociously hard to read markup generated by some specialized HTML editors and conversion tools, and can help you identify where you need to pay further attention to making your pages more accessible to people with disabilities. Tidy further provides a simple way to convert HTML to well formed XML, see WD-html-in-xml.
HTML-XML-utils
A number of simple C programs for manipulating HTML & XML: number headings, make a table of contents, make an index, manage bibliographic references (a simple implementation of refer(1) for HTML), list all links, create cross-references, extract elements that match a (CSS) selector, etc. Most are meant to be used in a Unix pipe or in shell scripts.
Ical2html - tools for icalendar files
The tools consist of three programs: ical2html reads an iCalendar (.ics) file, extracts all events between certain dates and of certain categories and creates an HTML page with monthly calendars; Icalfilter filters out events of a given category; icalmerge merges two or more iCalendar files, keeping only the most recent versions of duplicate events.
IsaViz
IsaViz is a visual environment for browsing and authoring RDF models represented as graphs.
Jigsaw - the Advanced Web Server
In June 1996, the release of Jigsaw demonstrated object-oriented web server design, written in Java. While it supports HTTP 1.1, traditional file-based resources, and CGI, its strength lies in its resource-based architecture. On this architecture, it supports advanced proxy caching features including ICP, Servlets, PICS, collaborative authoring, and more.
Libwww - the W3C Protocol Library
Libwww is a highly modular, general-purpose client side Web API written in C for Unix and Windows (Win32). It's well suited for both small and large applications. Pluggable modules provided with libwww include complete HTTP/1.1 (with caching, pipelining, PUT, POST, Digest Authentication, deflate, etc.), MySQL logging, FTP, HTML/4, XML (expat), RDF (SiRPAC), and much more. The purpose of libwww is to serve as a testbed for protocol experiments.
Note: In addition to the W3C Software License, libwww is covered by a specific notice, which includes CERN.
Link Checker
The W3C Link Checker checks that all the links in your HTML document are valid. There is a command-line interface and an online version. The Link Checker can easily be installed on one's server.
Log Validator
The Log Validator is a web server log analysis and validation tool: it can help web content managers find and fix the most frequently accessed invalid documents on their Web site. It is based on a flexible perl library that can be used to process lists of Web documents for validation or other tasks.
Markup Validation Service
The W3C Markup Validation Service, also known simply as “HTML Validator” is a free online service that helps check Web documents in languages such as HTML, XHTML, SVG, MathML, etc. Its source code is also available, and it is relatively easy to install on a number of platforms.
mobileOK checker library
The W3C mobileOK checker Java library helps building applications that can assess whether a Web page is mobileOK Basic, highlighting potential problems it would have to be used on a mobile device (such as a phone or a PDA). It serves as a successor to the mobile web best practices checker.
RDFPic
RDFPic is a tool to embed an RDF description of a picture into the picture itself, as described by Describing and retrieving photos using RDF and HTTP. The version in CVS supports XMP.
RDF Validator
The RDF Validator checks the syntax of RDF documents, and can produce a graph of any RDF data. Its java code can run as a java servlet with jetty, tomcat or Jigsaw. Installation instructions for Jetty or Tomcat are available on the ESW Wiki.
XSV
XSV is a validator for W3C XML Schema, available both for download in source and executable formats, and online.
web-platform-tests (WPT)
web-platform-tests is a W3C-coordinated effort to build a cross-browser testsuite for the majority of the Web platform. Its goal is to help achieve interoperability among different implementations.
HcalProxy
Hcalproxy runs as a personal proxy and converts (remote) HTML with hCalendar microformat mark-up to icalendar. For example, if http://example.org/ex.html is an HTML document, then http://localhost:8000/http://example.org/ex.html is an icalendar document with all events from that HTML document.
rdjpgxmp, wrjpgxmp, xmptool
rdjpgxmp and wrjpgxmp extract and insert XMP data in JPEG (JFIF) files. xmptool can print the value of a particular property in an XMP file, delete a property from an XMP file, or insert a property/value pair into an XMP file.
Recut
Recut is like the well-known cut utility in Unix, but it can also duplicate and reorder fields. E.g., if you do cut -f2,2,1 myfile you get fields 1 and 2 from myfile. The order is ignored and so are duplicates. But with recut -f2,2,1 myfile you get field 2, field 2 again, and field 1, in that order.
Unicorn
Unicorn is W3C's unified validator, which helps people improve the quality of their Web pages by performing a variety of checks. Unicorn gathers the results of the popular HTML and CSS validators, as well as other useful services.
csvtotab & tabtocsv
Csvtotab converts files of tabular data in comma-separated values (CSV) to tab-separated values, tabtocsv does the opposite. They are intended to be compliant with Model for Tabular Data and Metadata on the Web.
mail-transcode
mail-transcode can convert e-mail messages between quoted-printable, base64 and binary encoding, which could be useful in e-mail filters.
Internationalization checker
This checker performs various tests on a Web page to determine its level of internationalization-friendliness. It also summarizes key internationalization information about a page, such as character encoding and language declarations.
AgendaBot
AgendaBot is an IRC robot that watches a channel, looking for lines of the form agenda: URL. It tries to parse the document at that URL and extract an agenda, which it then prints on IRC. It understands a few different formats. AgendaBot is especially useful as a complement to Zakim (but doesn't depend on Zakim).
scribe.perl (v2)
scribe.perl is a Perl script that converts IRC logs (such as those made by RRSAgent, but also other IRC clients) to nicely formatted HTML. It knows about various conventions that are used by W3C groups to describe action items, agenda items, list of participants, etc.
zakim-monitor
Zakim-monitor is a (Perl) program that displays a table in a text terminal (such as an xterm or a MacOS Terminal) with the current agenda, speaker queue and open questions from an IRC channel that is managed by the Zakim IRC bot. It does that by connecting to the IRC channel and watching for messages from the Zakim bot. After each message, it updates the information displayed in the terminal.
GHURLBot a.k.a “gb”
GHURLBot (for “GitHub URL Bot”) is an experimental IRC bot that usually runs under the name “gb”. It can find the URLs of GitHub issues, look up issue summaries and create new issues and action items. (An “action item” is an issue that has an assigned person and a deadline.) It does a similar job as Trackbot, but for GitHub issues, rather than Tracker issues.
gf-markdown-awk
A library for Awk programs that provides functions to convert GitHub-flavored markdown to HTML, to inline HTML, or to plain text.
Past Projects
Here is the list of Past Open Source Projects developed at W3C.
Get involved! Contribute to W3C Open-Source Software
W3C software is free and open source: the software is made primarily by people of the Web community, for the Web community.
There are many ways to get involved:](https://www.w3.org/Status)

Help Others
Great communities make great tools, and with only a few minutes of your time you can join the mailing-lists associated with W3C open source projects (such as www-validator for the markup validator or www-validator-css for the CSS validator) and participate in discussions and user support.

A lot of W3C software have a specific user discussion mailing-list (see each projects for details), some also have IRC (chat) channels, such as the #validator channel on the irc.freenode.net for discussions on W3C validation services.

Write code
Developers are welcome to get involved by contributing code. either to existing projects (see list above and check each project's documentation for contact e-mail information), or proposed future software. Patches and bug fixes are always welcome, and developers willing to get seriously involved will generally get commit access after a proving period.

As explained below, all of W3C software source is freely available, developers are encouraged to get the source for the projects they care about and start hacking right away.

Read the IPR FAQ on software contribution if you intend to contribute code. Note that as this license is GPL compatible, it is possible to redistribute software based on W3C sources under a GPL license.

Send Feedback
Code is not the only way to get involved in making W3C software better. Testing, bug reports, suggestions, or help in creating good documentation are equally important! Most project will have a Feedback page, and you can report bugs, test cases and patches on our Bugzilla.

Donate
All the tools listed on this page are free and open source, but hosting, maintaining and developing them often costs a lot. With your support through the Validator Donation Program or the W3C Supporters Program, we can build even better tools.

Download and Check source code
Most W3C software is available directly from our CVS base or in our Mercurial repository. You can browse the content and history of either through their respective web interfaces.

See the documentation of each software for specific instructions for download and installation.

Some software that was formerly available via FTP at ftp.w3.org has been moved to our web site.

Page maintained by W3C Systems Team and individual software authors $Date: 2025/11/21 22:52:59 $
Copyright © 1994-2024 W3C®. W3C liability, trademark, document use and software licensing rules apply. Your interactions with this site are in accordance with our public and Member privacy statements.
