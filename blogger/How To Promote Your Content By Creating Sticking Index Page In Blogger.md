
##### [Awesome Tips Series about Blogger](https://lifelongprogrammer.blogspot.com/search/label/Blogger_Series){target="blank"}
<script src="https://lifelongprogrammer.blogspot.com/feeds/posts/default/-/Blogger_Series?orderby=updated&amp;alt=json-in-script&amp;callback=series&amp;max-results=20"></script>

---

#### TL;DR
- How to create a page which includes posts you would like to promote.
- Stick it in your blogger.
- Create a Custom "Page Not Found" to promote Posts.

#### Create an automatically updated index page
- Include Sections about **New Posts**, **Recently Updated Posts**, **New Posts based on Labels**

##### The Implementation
- Based on the code from [here](https://www.howbloggerz.com/2017/03/generate-html-sitemap-page-blogger.html)
``` {.html .numberLines .lineAnchors}
<script type="text/javascript">
  //<![CDATA[  
  const newPublishedPosts = new Set();
  function showNewPosts(json) {
    var toIgnoreSet = new Set();
    showPostsImpl(json, 20, toIgnoreSet, newPublishedPosts)
  }
  function showUpdatedPosts(json) {
    var toIgnoreSet = newPublishedPosts;
    showPostsImpl(json, 10, toIgnoreSet);
  }
  function showPosts(json, totalposts, toIgnoreSet, addedSet) {
    showPostsImpl(json, 1000);
  }  
  function showPostsImpl(json, totalposts, toIgnoreSet, addedSet) {
    for (var count = 0, publishedCount=0; publishedCount < totalposts && count< json.feed.entry.length ; count++) {
      var entry = json.feed.entry[count];
      var postTitle = entry.title.$t;
      var posturl;
      // if (count == json.feed.entry.length) break;
      for (var b = 0; b < entry.link.length; b++) {
        if (entry.link[b].rel == 'alternate') {
          posturl = entry.link[b].href;
          break;
        }
      }
      if(postTitle == "home") continue;
      if(postTitle.toLowerCase().startsWith("draft")) continue;
      if(toIgnoreSet && toIgnoreSet.has(postTitle)) continue;
      if(addedSet) addedSet.add(postTitle)
      publishedCount++;
      document.write('<li>');
      document.write(postTitle.link(posturl));
      document.write('</li>');
    }
  }
  //]]>    
</script>
<br />
<h3>Popular Posts</h3>
<script src="https://lifelongprogrammer.blogspot.com/feeds/posts/default/-/Promo-Main?orderby=updated&amp;alt=json-in-script&amp;callback=showNewPosts&amp;max-results=10"></script>

<br />
<h3>New Posts</h3>
<script src="https://lifelongprogrammer.blogspot.com/feeds/posts/default/?orderby=published&amp;alt=json-in-script&amp;callback=showNewPosts&amp;max-results=21"></script>

<br />
<h3>Updated Posts</h3>
<script src="https://lifelongprogrammer.blogspot.com/feeds/posts/default/?orderby=updated&amp;alt=json-in-script&amp;callback=showUpdatedPosts&amp;max-results=31"></script>

<br />
<h2>Development</h2>
<h3><a href="/search/label/Dev%20Tips">Dev Tips</a></h3>
<script src="https://lifelongprogrammer.blogspot.com/feeds/posts/default/-/Dev Tips?orderby=updated&amp;alt=json-in-script&amp;callback=showPosts&amp;max-results=20"></script>
```

#### [Make a Sticky Post in Blogger](https://www.wikihow.com/Make-a-Sticky-Post-in-Blogger)
- Publish the post first then change date to a future date

#### [Create a Custom "Page Not Found" to promote Posts]((https://lifelongprogrammer.blogspot.com/2019/06/promote-your-content-by-creating-a-custom-page-not-found-in-blogger.html){target="blank"})<a name="page_not_found"></a>
- Check [here for more detail](https://lifelongprogrammer.blogspot.com/2019/06/promote-your-content-by-creating-a-custom-page-not-found-in-blogger.html){target="blank"}

#### Resources
- [How To Generate HTML Sitemap Page On Blogger](https://www.howbloggerz.com/2017/03/generate-html-sitemap-page-blogger.html)

---

#### [Related Posts](https://lifelongprogrammer.blogspot.com/search/label/Blogger)<a name="related"></a>
<script src="https://lifelongprogrammer.blogspot.com/feeds/posts/default/-/Blogger?orderby=updated&amp;alt=json-in-script&amp;callback=weightedRandomRelatedPosts&amp;max-results=20"></script>
<script src="https://lifelongprogrammer.blogspot.com/feeds/posts/default/-/Google?orderby=updated&amp;alt=json-in-script&amp;callback=weightedRandomRelatedPosts&amp;max-results=20"></script>