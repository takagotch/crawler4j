### crawler4j
---
https://github.com/yasserg/crawler4j

```java
public class Mycrawler extends WebCrawler {
  private final static Pattern FILTERS = Pattern.compile(".*(\\.(css|js|gif|jpg"
    + "|png|mp3|mp4|zip|gz))$");
  
  @Override
  public boolean shouldVisit(Page referringPage, WebURL url) {
    String href = url.getURL().toLowerCase();
    return !FILTERS.matcher(href).matches()
      && href.startsWith("https://www.ics.uci.edu/");
  }
  
  @Override
  public void visit(Page page) {
    String url = page.getWebURL().getURL();
    System.out.println("URL: " + url);
    
    if (page.getParseData() instanceof HtmlParseData) {
      HtmlParseData htmlParseData = (HtmlParseData) page.getParseData();
      String text = htmlParseData.getText();
      String html = htmlParseData.getHtml();
      Set<WebURL> links = htmlParseData.getOutgointUrls();
      
      System.out.println("Text length: " + text.length());
      System.out.println("Html length: " + html.length());
      System.out.println("Number of outgoing links: " + links.size());
    }
  }
}




```

```
```

```
```


