# Speaker Notes

## Brief History Lesson

First there were static sites, essentially just a large collection of documents linked together, either they were just HTML or HTML with say PHP which was rendered on a server and pushed to the client.  
Then, as JavaScript and AJAX were developed, sites could now send data back to the server after the page had been loaded. Sites became more interactive. Think of your eCommerce type site where you could now add a product to your cart.  
Now, there’s a trend towards Single Page Apps which are JavaScript apps which are pushed to the client, bootstrapped, and then run entirely on the client, only communicating with the server to fetch and push data. Things like routing and page transitions are handled by the client. This gives a quicker experience since you don’t have to make a network request every time you visit another page.

## What are PWA's?

These are web apps that run in the browser.

## Today's Problems

There are a few problems we’ve encountered today with Native Apps and Native App markets.

## App Distribution & Support

The first is app distribution and support. There’s a talk from O’Reilly’s Fluent conference (https://www.oreilly.com/ideas/progressive-web-apps-and-whats-next-for-mobile) that talks about how the way software is distributed affects how software is developed. Think in the past, you were limited to what you could fit on a floppy disk, or multiple floppies. Today, with Native Apps, you’re at the hands of the Apple App Store or the Google Play Store. When you make an update to your code, you have to push an update, which only some of your users will actually install. That means your production code powering those apps now has to accommodate for multiple versions coexisting at once. If you can simulate an app experience in a web app, now you only have to support one version of the code since you can perform the updates behind the scenes without users having to actively manage those updates. I guess one of the downsides is you can’t have lit update messages now.

## Global Cellular Networks

This is from a report by Ericcson (https://www.ericsson.com/res/docs/2015/ericsson-mobility-report-june-2015.pdf) about global cell usage. Green means 4G, purple means 3G, and blue means 2G. You can see that a majority of the world still runs on 2G and 3G networks today and will still run on them for years to come. So data speeds and connectivity pose some challenges. And even so, cell networks can’t reach everywhere - if you’re underground, say in a subway, or you’re just in the middle of nowhere, you’re not going to have the greatest service. Cell networks right now are not quite as reliable as a wired Internet connection or even Wifi.

## Zombie Apps

There are over a million apps you can download for your phone, but most are never discovered and never used. TechCrunch reports (https://techcrunch.com/2015/01/30/zombie-apps-on-the-rise-83-of-apps-not-on-top-lists-up-from-74-last-year/) that 83% of apps never reach the top 300 lists. And the apps that you do download, most just serve as a replacement for the web experience, ripe candidates for pwa’s. And Apps are less discoverable on search engines and their internal pages aren’t able to be indexed.

## Add to Home Screen

Add to home screen allows you to make an icon on your home screen which will launch the website when you tap it. Apps that support this will show ‘Add to Homescreen’ popups. All of this is powered by a manifest JSON file which defines things like the app name, start URL, icon, and splash screen color. This isn’t necessarily a new concept - mobile Safari has had something similar to this for a while now.

## Push Notifications

With new Push APIs, you can now trigger push notifications through the web browser.

## Work Offline

This is mainly powered by caching data in LocalStorage or IndexedDB. Therefore when you’re offline, it will serve you this data so you can still interact with some of the app that you may have previously interacted with. For something like Hacker News, you would be able to see the comments of links you’ve visited.

This also includes service workers which can run background tasks. This allows for things like syncing your app state when you go offline and back online. They also let you do some neat stuff and Polymer has some neat tools for this (https://www.polymer-project.org/1.0/toolbox/) that let you race fetching content - you can race between the network and cache and whichever is faster will be used.

## Fast Interactivity

There’s a statistic that 53% of users abandon a web site if it takes longer than 3 seconds to load. So it’s imperative for these web apps to load quickly. Much of this performance gain is aided by caching but also due to a special kind of architecture called the App Shell architecture. The idea here is that you first send down the most important HTML and CSS which defines the “shell” of your app and then dynamically load the content in afterwards. And on repeat visits because of caching, the app can load incredibly fast.  
But what exists is this uncanny valley before the JavaScript loads - you try interacting but your taps don’t do anything. With better performance optimizations this time can be reduced; you can also make common touch points like navigation out of CSS so that they’re still usable, but then once the JavaScript loads, more interactivity can happen. Two key terms here are ‘time to first paint’ and ‘time to first meaningful paint’  
One of the successful examples here is Flipkart which is a marketplace popular in India. Rewriting their mobile app to a PWA increased conversions by 70% (https://developers.google.com/web/showcase/2016/flipkart).  
You can also speed up interactivity by code splitting and loading modules as you visit the pages that need them. Module bundlers like webpack allow you to do this.  
This is all summarized in what’s called the PRPL pattern (https://developers.google.com/web/fundamentals/performance/prpl-pattern/).  
- Push critical resources for the initial URL route.
- Render initial route.
- Pre-cache remaining routes.
- Lazy-load and create remaining routes on demand.

## Tools

Also Google Chrome Dev Tools ‘Application’ Tab

## Resources

Addy Osmani is one of the people at Google advocating for PWA’s. He’s got some great talks and articles about actually making SPA’s progressive in frameworks like React, Angular, Ember, and Polymer.  
And there’s more resources about what PWA’s are.
