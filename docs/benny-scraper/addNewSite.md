---
layout: default
title: Adding New Sites to Benny-Scraper
---

# Adding New Sites to Benny-Scraper

Guidelines and steps on how to integrate and add new sites to the scraper.

## Table of Contents
1. [Step 1: Identify the Site](#step-1-identify-the-site)
2. [Step 2: Configure appsettings.json](#step-2-configure-appsettingsjson)



#### Step 1: Identify the Site

For this, we will use [Issue 40](https://github.com/martial-god/Benny-Scraper/issues/40) as an example. The issue is was orginally brought up "Please add [noveldrama.com Virginity in Second Marriages](https://noveldrama.com/virginity-in-second-marriages-bd6512.html#chapter-list)".

#### Step 2: Configure appsettings.json
A new edition will need to be added to the `appsettings.json`. The changes I made below mostly made use of copying the default xpath values provided by the browswers' **Dev tools**, cases like `chapterContent` and `chapterContentImageUrlAttribute` are not included in the default values and will need to be added manually.

```json
    {
    "name": "noveldrama", // name of site
    "urlPattern": "noveldrama.com", // url pattern to match
    "hasPagination": true, // does the site have pagination i.e. page 1, page 2, page 3 etc
    "paginationType": "?page={0}", // the type of pagination i.e. ?page=1, ?page=2, ?page=3 etc. Should be null if no pagination
    "paginationQueryPartial": "?page=", // the query partial for pagination i.e. ?page=, ?page=, ?page= etc. Should be null if no pagination
    "hasNovelInfoOnDifferentPage": false, // does the site have novel info on a different page than the chapters, https://lighnovelheaven.com/novel/the-legendary-mechanic/ for example.
    "chaptersPerPage": 36, // how many chapters are on each page of the table of contents if there is pagination. Should be -1 if no pagination
    "pageOffSet": 1, // the page offset for the table of contents i.e. if the first page is 0 or 1. Should be 0 if the first page is 0 and 1 if the first page is 1
    "completedStatus": "completed", // the status of the novel if it is completed or not as shown on the site
    "hasImagesForChapterContent": false, // should be true if the chapter content has images and false if it does not, i.e. for comic or manga sites
    "isSeleniumSite": false, // meant for sites that require a user to be logged in. Not used yet; sites like webnovel.com or wuxiaworld.com.
    "selectors": {
        // START OF NOVEL SPECIFIC SELECTORS
        "chapterLinks": "//*[@id='chapter-list']/tbody/tr[1]/td[1]/div/a", // the xpath for an individual chapter link
        "tableOfContentsPaginationListItems": "//div[@class='pagination-container']/ul/li", // the xpath for the pagination list items. Should be null if no pagination
        "lastTableOfContentsPage": "//li[@class='PagedList-skipToLast']//a/@href", // the xpath for the "last page" button of the table of contents. Should be null if no pagination
        "lastTableOfContentPageNumberAttribute": "href", // the attribute of the "last page" button that contains the page link. Should be null if no pagination
        "latestChapterLink": "/html/body/section[2]/div/div[1]/div[1]/div/div/div[2]/table/tbody/tr[6]/td[2]/a", // the xpath for the latest chapter link
        "novelStatus": "/html/body/section[2]/div/div[1]/div[1]/div/div/div[2]/table/tbody/tr[5]/td[2]",
        "novelAuthor": "/html/body/section[2]/div/div[1]/div[1]/div/div/div[2]/table/tbody/tr[1]/td[2]/a/text()", // the "/text()" at the end is to get the text of the element
        "novelAlternativeNames": null,
        "novelGenres": "/html/body/section[2]/div/div[1]/div[1]/div/div/div[2]/table/tbody/tr[2]/td[2]/a/text()",
        "novelRating": null,
        "novelTitle": "/html/body/section[2]/div/div[1]/div[1]/div/div/div[2]/h1",
        "totalRatings": null,
        "novelDescription": "//div[@id='bookinfo']//p | //div[@id='bookinfo']//h2", // the xpath for the novel description, *NOTE* this sie had different elements for the description
        "novelThumbnailUrl": "/html/body/section[2]/div/div[1]/div[1]/div/div/div[1]/div/div/img", // the xpath for the novel's thumbnail url
        "thumbnailUrlAttribute": "src", // the attribute of the thumbnail url element that contains the url
        // START OF CHAPTER SPECIFIC SELECTORS
        "chapterTitle": "/html/body/section[2]/div/div[1]/div/div/h2",
        "chapterContent": "//div[contains(@class, 'readerbody-wg')]//p", // the xpath for the chapter content, "//p" is used to get all the <p> elements
        "alternativeChapterContent": "//p", // the xpath for the chapter content if the chapter content is not in a <p> element, keep as "//p" if the chapter content is in a <p> element
        "chapterContentImageUrlAttribute": null // should be null if the chapters do not have images
    }
```
Description of the second step...

... (and so on for each step)
