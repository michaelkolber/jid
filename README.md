# JID
A Javascript bookmarklet that tells you the JID of the page you're on. Currently tested on Google Chrome 51.0.2704.106, on [cvisiontech.com](http://cvisiontech.com).

##How-To
1. Right click the bookmarks bar.
2. Click "Add page..."
3. Type in a name (such as "Check JID").
4. Paste the following into the URL field:

        javascript:(function() { var v = '3.1.0'; if (window.jQuery === undefined || window.jQuery.fn.jquery < v) { var done = false; var script = document.createElement('script'); script.src = 'http://ajax.googleapis.com/ajax/libs/jquery/' + v + '/jquery.min.js'; script.onload = script.onreadystatechange = function() { if (!done && (!this.readyState || this.readyState == 'loaded' || this.readyState == 'complete')) { done = true; initMyBookmarklet(); } }; document.getElementsByTagName('head')[0].appendChild(script); } else { initMyBookmarklet(); } function initMyBookmarklet() { var fullNode = jQuery('.feature').last().contents(); var comment = fullNode[1].textContent; var separated = comment.split('&'); var chunk = separated[2].split('='); console.log('Page JID: ' + chunk[1]); alert('Page JID: ' + chunk[1]); } })();)

That's it!
