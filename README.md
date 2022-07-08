# test-task-for-build
a type of work and challenges that are aligned with our everyday tasks while supporting customers, business partners, and ISVs.

## Description of the task:
- please prepare a PoC solution (so understandably brief and with a limited functionality, reliability, recovery) that fulfills the following requirements and features:

Description of the task based on Serverless Swift book example - instead of Swift language prepare it in any other suitable language (preferably JAVA, JS, Python, GO, C#) - see https://github.com/serverless-swift/ch6-app and if possible a chapter 6 of the book in the library here: https://www.oreilly.com/library/view/serverless-swift-apache/9781484258361/:
- please prepare a PoC solution (so understandably brief and with a limited functionality, reliability, recovery) that fulfills the following requirements and features:


### Functional Requirements
- an application - or a microservice needs to query a public API (accessible from any public site - see the example of the api call for HackerNews: 
 let request - the call that gets all the top articles from HackerNews: query https://hacker-news.firebaseio.com/v0/topstories.json

```swift 
 [ClientRequest.Options] = [ 
        .method("GET"),
        .schema("https://"),
        .hostname("hacker-news.firebaseio.com"),
        .path("/v0/topstories.json")
]
```

and then you can get the details of each of the articles - for example calling details for the article here: https://hacker-news.firebaseio.com/v0/item/23304614.json

```swift
    //make an API call to Hacker News - check the link for the given id alike HN article: 23304614
    //let apiUrlTop100HNIds = "https://hacker-news.firebaseio.com/v0/item/23304614.json"
    let request: [ClientRequest.Options] = [ 
        .method("GET"),
        .schema("https://"),
        .hostname("hacker-news.firebaseio.com"),
        .path("/v0/item/\(param.newsId as! String).json")
    ]
)
```

- the microservice needs to page (parse through the pagination of results) automatically through the JSON pages produced by API (there might be 20-40 results in a JSON array per page);
- the resulted records are stored in the destination - SaaS DB (NoSQL DB - Cloudant), or Object Storage;
- the refresh allows for checking for the new documents in the results and insert the delta in the destination storage - specified above
- (optional) extra points for adding the Watson Natural Language analysis of the documents (via provided URL), and adding the resulting tags for Concepts, Keywoards, Entities to the existing document records - check more details here: https://cloud.ibm.com/catalog/services/natural-language-understanding
- there should be a simple UI to invoke the microservice to read a record, and initialize pulling of the documents from API


### Non Functional Requirements
- the microservice - an internal API - needs to be a container (so application needs to be containerized app with a Dockerfile) deployed in a K8s cluster or in OCP in IBM Cloud (extra brownie points for S2I - but it is not necessary!)
- the storage needs to be spun in IBM Cloud - IBM Cloudant, or Object Storage in IBM Cloud;
- optionally you might use a different storage/DB - all the choices need to be discussed;
- all the tasks should be possible with free of charge tier in IBM Cloud: https://cloud.ibm.com

