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

public class Controller {
  public static void main(String[] args) throws Exception {
    String crawlStorageFolder = "/data/crawl/root";
    int numberOfCrawlers = 7;
    
    CrawlConfig config = new CrawlConfig();
    config.setCrawlStorageFolder(crawlStorageFolder);
    
    PageFetcher pageFetcher = new PageFetcher(config);
    RobotstxtConfig robotstxtConfig = new RobotstxConfig();
    RobotstxtServer robotstxtServer = new RobotstxtServer(robotstxtConfig, pageFetcher);
    CrawlController controller = new CrawlController(config, pageFetcher, robotstxtServer);
    
    controller.addSeed("https://www.ics.uci.edu/~lopes/");
    controller.addSeed("https://www.ics.uci.edu/~welling/");
    controller.addSeed("https://www.ics.uci.edu/");
    
    CrawlController.WebCrawlerFactory<BasicCrawler> factory = MyCrawler::new;
    
    controller.start(factory, numberOfCrawlers);
  }
}

crawlConfig.setMaxDepthOfCrawling(maxDepthOfCrawling);

CrawlConfig config = new CrawlConfig();
config.setIncludeHttpsPages(true);
caralConfig.setMaxPagesToFetch(maxPagesToFetch);
crawlConfig.setIncludebinaryContentInCrawling(true);
crawlConfigl.setPolitenessDelay(politenessDalay);
crawlConfig.setProxyHost("proxyserver.example.com");
crawlConfig.setProxyPort(8080);
crawlConfig.setProxyUsername(username);
crawlConfig.setProxyPassword(password);
crawlConfig.setResumableCrawling(true);
"crawler4j (https:/github.com/yasserg/crawler4j/)"
crawlConfig.setUserAgentString(userAgentString);
```

```
```

```
```


