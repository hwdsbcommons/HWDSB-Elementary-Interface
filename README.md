Forked for Brightspace VLE: Responsive Full Width Tabs (from Codrops Blueprints)
=========

1. Upload the entire contents of the repo into Shared Files, in a directory named "fullwidthtabs"

1. The below code goes in a widget at the root of your Learning Environment and is then shared with courses as appropriate (I've left the CDATA nonsense that Brightspace inserts as it attempts to sanitize the code so you aren't puzzled when the code changes):

```
<script>// <![CDATA[
(function() {
			    var contentFile = '/shared/fullwidthtabs/index.html';
			    var iframe = document.createElement('iframe');
			    iframe.addEventListener('load', function() {
			      var orgUnitId = {orgUnitId}; // this uses LE replace-strings
			      iframe.contentWindow.start(orgUnitId);
			    });
			    iframe.style.width = '100%';
			    iframe.style.height = '700px';
			    iframe.src = contentFile;
			    document.currentScript.parentNode.insertBefore(iframe, document.currentScript);
			  })();
// ]]></script>
```

Then identify each LTI link that requires an {orgUnitID} token with its own id in the HTML

EG: 
```
<div class="mediabox"><a id="mindomoLink" href="/content/" target="_blank"><img src="img/smallermindomo.png" alt="Mindomo Logo" /></a>
<h3>Mindomo</h3>
</div>
```


That URL is then constructed by the "function start(orgUnitId)" javascript function at the bottom of index.html

```
document.getElementById("mindomoLink").href = "https://hwdsb.elearningontario.ca/d2l/common/dialogs/quickLink/quickLink.d2l?ou=" + orgUnitId + "&type=lti&rcode=eLO-9882434&srcou=7587";
```

##Credits, Props, Thanks:

Codrops Readme: 

100% width tabbed content with some example media queries for smaller screens. 

[article on Codrops](http://tympanus.net/codrops/?p=18521)

[demo](http://tympanus.net/Blueprints/FullWidthTabs/)

The Blueprints are a collection of basic and minimal website concepts, components, plugins and layouts with minimal style for easy adaption and usage, or simply for inspiration.
Check out all of our Blueprints [here](http://tympanus.net/codrops/category/blueprints/)

Integrate or build upon it for free in your personal or commercial projects. Don't republish, redistribute or sell "as-is". 

Read more here: [License](http://tympanus.net/codrops/licensing/)

[© Codrops 2013](http://www.codrops.com)
