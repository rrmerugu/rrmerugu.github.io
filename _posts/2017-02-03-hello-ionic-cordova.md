---
layout: post
title: Hello Ionic framework - a sample hydrib mobile application.
---


[Ionic Framework](https://ionicframework.com/) as the website says is 
the top open source framework for building amazing mobile apps..

I've written a sample 3 page mobile app that can be deployed into `iOS` and `android`.


<!--/excerpt-->

Here is how to use it and code is hosted at [https://github.com/rrmerugu/hello-ionic](https://github.com/rrmerugu/hello-ionic).
 
1. Step1: Create ionic app `ionic start hello_app --v2 sidemenu`

2. Step2: Create new page `ionic g page home`

3. Step3: Configuring the pages in the app
    - Add new page `home` in `src/app/app.module.ts` 
    - Import and add `home` in `src/app/app.components.ts`
    - Pages of the app is located in `src/app/app.components.ts` with variable 
    in `this.pages`
    - Change the index/root page of the app in `src/app/app.components.ts` with the variable 
    `rootPage`. Change the `rootPage` variable accordingly.
    - SideMenu template can be found at `src/app/app.html`
4. Generating a build for `iOS` `ionic build ios`. App is generated in 
`hello-ionic/hello_app/platforms/ios/build/emulator/hello_app.app`
5. Simulating the generating build using `ionic emulate ios`



## Other commands 

- `ionic platforms` to check the available platforms
- `ionic platform add android` to add android platform



### Publishing 


- Remove any `plugins` that you used for development but not needed for production. 
Example: `cordova plugin rm cordova-plugin-console`
- Creating a production build - `ionic build ios --release`




## References:
- Anatomy of Code : https://ionicframework.com/docs/v2/setup/tutorial/project-structure/
- Generate page : https://ionicframework.com/docs/v2/cli/generate/
- Create to Deployment Guide : https://ionicframework.com/docs/guide/ 
- Publishing in android and iOS: https://ionicframework.com/docs/guide/publishing.html


Try it out. All the very best :)
