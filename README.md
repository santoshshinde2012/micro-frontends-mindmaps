# Micro-Frontend Mindmaps

#### What

In this repository, you will find mindmaps we created about Micro-Frontend based on public information. As all of the information is already in the public domain, please feel free to use and share these mindmaps however you like.  

#### What is Micro-Frontend ?

Micro-frontends are the technical representation of a business subdomain, they allow independent implementation with the same and different technology.

Please find the key factors for micro-frontends below.

- Decomposed
- Independent
- Tech-Agnostic
- Deployable Separately
- Loosely Coupled
- Customizable
- Updated Incrementally
- Fault-Tolerant



#### The History of Microfrontends

![The History of Microfrontends](assets/mf-history.png)
![The History of Microfrontends](assets/micro-frontend-history.png)


- 2011: Microservices
- 2016: [Thought Works added Micro frontends to the technology radar](https://www.thoughtworks.com/radar/techniques/micro-frontends)
- Nov 2017: [Thought Works recommended Single-Spa for Micro-frontends implementation](https://www.thoughtworks.com/en-in/radar/languages-and-frameworks/single-spa)
- 2019: [Martin Fowler wrote his article about Micro-frontends and promoted Micro-frontends architecture in his article “Micro Frontends.”](https://martinfowler.com/articles/micro-frontends.html)
- Apr 2020: [We see microfrontend architect design as a trend early in 2020 - Software Architecture and Design InfoQ Trends](https://www.infoq.com/articles/architecture-trends-2020/)
- Oct 2020: [By the end of 2020, Zack Jackson released his masterpiece “Module Federation” as a plugin in Webpack 5](https://webpack.js.org/concepts/module-federation/)
- 2021: Discovery
- Apr 2021: [Thought-works started to recommend Module Federation for Micro-frontends implementations](https://www.thoughtworks.com/radar/languages-and-frameworks/webpack-5-module-federation)

#### Micro-frontends decisions framework

The 4 pillars that we need to decide up-front when architecting micro-frontends, as stated by [Luca Mezzalira](https://github.com/lucamezzalira) here in his medium article - [Micro-frontends decisions framework](https://medium.com/@lucamezzalira/micro-frontends-decisions-framework-ebcd22256513).

```mermaid
graph TD;
  A1[Micro-frontends decisions framework]-->B1[Definition];
  A1[Micro-frontends decisions framework]-->B2[Composition];
  A1[Micro-frontends decisions framework]-->B3[Route];
  A1[Micro-frontends decisions framework]-->B4[Communication];
```

#### Defining Micro-Frontends

Identifying micro-frontends becomes quite straightforward. Understanding how users behave is of great use in determining our micro-frontends. You can read Luca Mezzalira's full article [here](https://medium.com/dazn-tech/identifying-micro-frontends-in-our-applications-4b4995f39257) for more details.

[Identifying micro-frontends in our applications](https://medium.com/dazn-tech/identifying-micro-frontends-in-our-applications-4b4995f39257)



```mermaid
graph TD;
  A1[Defining Micro-Frontends]-->B1[Horizontal split];
  A1[Defining Micro-Frontends]-->B2[Vertical split];
  B1--Domain Driven Design-->C1[Core Subdomains]
  B1--Domain Driven Design-->C2[Supporting Subdomains]
  B1--Domain Driven Design-->C3[Generic Subdomains]
  B2--Domain Driven Design-->C1[Core Subdomains]
  B2--Domain Driven Design-->C2[Supporting Subdomains]
  B2--Domain Driven Design-->C3[Generic Subdomains]
```


#### Composition of Micro-frontends

Analyzing how different frameworks can be used with different micro frontends on the same page.

```mermaid
graph TD;
  A[Composition of Micro-frontends]-->A1[Client-side composition];
  A[Composition of Micro-frontends]-->A2[Edge-side composition];
  A[Composition of Micro-frontends]-->A3[Server-side composition];
  A[Composition of Micro-frontends]-->A4[Build Time Composition];
```

##### 1. Client-side composition

Client Side Composition is one of the patterns that combine Fragments on client-side

```mermaid
graph TD;
  A1[Client-side composition]-->B1[Fragments]
  A1[Client-side composition]-->B2[Libraries]
  B2[Libraries]-->C1[single-spa/single-spa]
  B2[Libraries]-->C2[frintjs/frint]
  B2[Libraries]-->C3[smapiot/piral]
```

##### 2. Edge-side composition
Basically its combination of client side and server side composition to take the advantages of CDN caching.
Idea behind edge-side composition – fragments are stitched together, close to the client. 

```mermaid
graph TD;
  A1[Edge-side composition]-->B1[Lambda Edge]
  A1[Edge-side composition]-->B2[Rendering Example]
  B1[Lambda Edge]-->C1[AWS Lambda CloudFront]
  B2[Rendering Example]-->D1[Next js using Lambda Edge and Serverless Framework]
  B2[Rendering Example]-->D2[Cloudflare Workers using a framework called Flareact]
```


##### 3. Server-side composition
Pattern that assembles Fragments on the server side.

```mermaid
graph TD;
  A1[Server-side composition]-->B1[Layout Server]
  A1[Server-side composition]-->B2[Fragments Server]
  A1[Server-side composition]-->B3[Fragment Gateway]
  A1[Server-side composition]-->B4[Libraries]
  B4[Libraries]-->C1[Ara Framework]
  B4[Libraries]-->C2[OpenComponents]
  B4[Libraries]-->C3[Piral]
  B4[Libraries]-->C4[Tailor]
```

##### 4. Build Time Composition
Build Time Composition assembles Fragments at build time, not at client or server. Publish each micro frontend as a package, and have the container application include them all as library dependencies.

```mermaid
graph TD;
  A1[Build Time Composition]-->B1[Shared libraries]
  A1[Build Time Composition]-->B2[Static Site Generators]
  A1[Build Time Composition]-->B3[Bit]
```

#### Micro-Frontends Communication

There are sometimes UI fragments belonging to different teams that need to interact or communicate. When a user adds an item to the basket by clicking the buy button, other micro frontends such as the mini basket want to be notified to update their content accordingly. 

##### 1. User interface communication

```mermaid
graph TD;
  A1[User interface communication]-->B1[Parent to fragment]
  A1[User interface communication]-->B2[Fragment to parent]
  A1[User interface communication]-->B3[Fragment to fragment]
  A1[User interface communication]-->B4[Publish Subscribe with the Broadcast Channel API]

```

##### 2. Sharing state

```mermaid
graph TD;
  A1[Sharing state]-->B1[Web Workers]
  A1[Sharing state]-->B2[Props and callbacks]
  A1[Sharing state]-->B3[Custom Events]
  A1[Sharing state]-->B4[Pub Sub library]
  A1[Sharing state]-->B5[Custom implementation]
```

#### Micro-Frontends Communication Patterns


##### 1. Parent to Fragment


```mermaid
graph TD;
  A1[Parent to Fragment]-->B1[Element Attributes]
  A1[Parent to Fragment]-->B2[Connected Callback]
  A1[Parent to Fragment]-->B3[Attribute Change Callback]
```

##### 2. Fragment to Parent

```mermaid
graph TD;
  A1[Fragment to Parent]-->B1[Custom Events]
  A1[Fragment to Parent]-->B2[Event Listeners]
```

##### 3. Fragment to Fragment

```mermaid
graph TD;
  A1[Fragment to Fragment]-->B1[DOM Manipulation]
  A1[Fragment to Fragment]-->B2[Attributes and Callbacks]
  A1[Fragment to Fragment]-->B3[Event Bus]
  A1[Fragment to Fragment]-->B4[Broadcast Channel API]
```

##### 4. Global Communication

```mermaid
graph TD;
  A1[Global Communication]-->B1[URL Params]
  A1[Fragment to Fragment]-->B2[Global Context and State]
  A1[Fragment to Fragment]-->B3[State Management Libraries Redux]
```


#### Micro-Frontends anti-patterns

- Difference between micro-frontend and component
- Multi frameworks approach
- Write programs that do thing and do it well
- Dependency hell
- Unidirectional flow at the rescue
- Avoid organizational coupling
- Multiple micro-frontends calling same endpoint

![4 Micro-Frontend Anti-Patterns](assets/four-micro-frontend-anti-patterns.jpeg)

##### 1. Difference between micro-frontend and component

A micro-frontend is a technical representation of a business subdomain that has a specific behavior that is controlled by the self.

A Component is a technical solution for any frontend element that has a specific behavior that may be modified by a controlled component or container.


| Component | Micro-Frontends |
| :---: | :---: | 
| Technical Solution | Technical Representation of business subdomain |
|  Having a specific behavior that may be modified by a controlled component or container. | Having some Behaviour but driven by self |


#### Implementation of  Micro Frontends

There are several ways to implement a microfrontend, and this article([3 Ways to Build Micro-Frontends](https://javascript.plainenglish.io/3-ways-to-develop-micro-frontends-in-2022-e29984158b6d)) will help you understand them.

According to my understanding, the application shell is the most crucial component of a micro-frontend architecture, as it is the component that enables you to render your all micro-frontends inside of a container.

###### Application shell

The application shell serves as the parent application to all micro-frontends. All incoming requests arrive there, It selects the micro-frontend that the user wishes to view and renders it in the <body> documents.

![Application shell](assets/micro-frontends-application-shell.jpg)

#### Micro Frontends Frameworks

1. [Bit](https://bit.dev/)
2. [Webpack 5 and Module Federation](https://webpack.js.org/concepts/module-federation/)
3. [Single SPA](https://single-spa.js.org/)
4. [Systemjs](https://github.com/systemjs/systemjs)
5. [Piral](https://github.com/smapiot/piral)
6. [Open Components](https://github.com/opencomponents/oc)
7. [Qiankun](https://github.com/umijs/qiankun)
8. [Luigi](https://luigi-project.io/)
9. [FrintJS](https://github.com/frintjs/frint)
10. [Mosaic 9](https://www.mosaic9.org/)
11. [PuzzleJS](https://github.com/puzzle-js/puzzle-js)


#### Microfrontends with Module Federation

Module federation allows a JavaScript application to dynamically run code from another bundle/build, on both client and server.

- loading the module (asynchronous)
- evaluating the module (synchronous)

##### Why Use Module Federation?

- Better way to share code : Expose any code from any application that Webpack supports.
- Environment-Independent : Use shared code in different environment web, Node.js etc.
- Resolves Dependency Issues : Federated code defines their dependencies and if Webpack can’t find it in the scope, will download it.
- Modernize Legacy Applications: The microfrontend approach divides a frontend into smaller, deployable parts, but is crucial for real-time scenarios with legacy applications and modernization, as companies may be reluctant to rewrite entire applications.

###### Advanced Topics

- Version Mismatches
- Dynamic Federation
- Mono vs. Multirepo
- Multiple Frameworks/Versions
#### [Summary](https://www.xmind.net/m/nfT7ef/) 

![Micro-Frontend Mindmap](assets/v1-microfrontend-mandmap.png)


### Case Studies

- [Experiences Using Micro Frontends at IKEA](https://www.infoq.com/news/2018/08/experiences-micro-frontends/)
- [What is a Micro Frontend? Examples and Mobile App Benefits](https://ionic.io/resources/articles/micro-frontends-for-mobile-with-ionic-portals)
  

#### When to use Micro Frontends ?

Each pattern, as we know, has advantages and disadvantages, and in order to use it, we must establish a boundary between these and our requirements.

- Ideal for large, fast-growing, and complex enterprise applications.
- Provides implementation independence, preventing blockages and bottlenecks.
- Ideal for independent deployments, allowing frequent updates without disrupting the entire application.
- Ideal for fast-paced environments requiring agility and quick response to changing marketing demands.
- Can accommodate different technology stacks, allowing teams to select the technology stack that best suits their needs
- Minimizes the risk of failure by detaching or detanglering different components of the application
- Enables collaboration between multiple, independent teams on a single application
- Creates a flexible application, allowing different configurations for different user types.
- Ideal for gradual modernization of existing solutions, allowing for gradual replacement of old components with micro-frontends.

#### References

1. [Mindmap](https://www.xmind.net/m/nfT7ef/)
2. [Behind leroymerlin.fr: Micro Frontends](https://medium.com/adeo-tech/behind-leroymerlin-fr-micro-frontends-47fd7c53f99d)
3. [Resources to start with Micro Frontend](https://gist.github.com/santoshshinde2012/ff346ae8aca26644fe15409847138e49)
4. [Micro Frontends Conference](https://hasgeek.com/jsfoo/microfrontends-conf/videos)
5. [Micro frontend resources](https://github.com/billyjov/microfrontend-resources)
6. [Four Micro-frontend Anti-patterns](https://blog.santoshshinde.com/four-micro-frontend-anti-patterns-58aaa9fe19d5)
7. [What’s the Difference Between a Component and a Micro-Frontend?](https://javascript.plainenglish.io/whats-the-difference-between-a-component-and-a-micro-frontend-43aefd0af062)
8. [Awesome Micro-Frontends](https://github.com/rajasegar/awesome-micro-frontends)
9. [Use React components inside Angular](https://github.com/microsoft/angular-react)
10. [Micro Frontend Architecture: Helping you move from theory to practice with our workshop](https://www.nearform.com/digital-community/micro-frontend-architecture-helping-you-move-from-theory-to-practice-with-our-workshop)
11. [Micro Frontends — The Better Way to Modernize Legacy Applications](https://medium.com/@johnlawrimore/micro-frontends-a-game-changing-strategy-for-legacy-app-migrations-6288f50a6f72)
12. [Micro frontend architecture](https://www.rst.software/blog/micro-frontend-architecture-101-what-is-it-when-to-use-it-and-how-to-migrate-your-existing-monolithic-app-in-9-steps)
13. [Microfrontends: Are We Solving Problems or Creating Them?](https://medium.com/gitconnected/microfrontends-are-we-solving-problems-or-creating-them-35f1098b0820?sk=6c4acc16fe754bfc09fd666db6dca08a)

#### Videos
1. [Micro-frontend Anti-patterns](https://www.youtube.com/watch?v=b9Zpi-oajA0)
2. [Micro-Frontends with Module Federation: Beyond the Basics](https://www.youtube.com/watch?v=tzXCrCwybgE)

#### Courses

1. [Microfrontends with React: A Complete Developer's Guide](https://www.udemy.com/course/microfrontend-course/learn/lecture/23206792#overview) by [Stephen Grider](https://www.linkedin.com/in/stephengrider)


### Recent Medium Posts

<table>
  <tr><th>Title</th><th>Categories</th></tr>
  <!-- BLOG-POST-LIST:START --><tr><td><a target='_blank' href=https://medium.com/@iMayank.Shekhar/level-up-your-micro-frontend-testing-with-cypress-plugins-a798faf8dbd3?source=rss------micro_frontends-5>Level Up Your Micro-Frontend Testing with Cypress Plugins</a></td><td><code>testing, micro-frontends, cypress</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@a.utkarsh_86098/building-react-apps-faster-with-rsbuild-my-journey-away-from-webpack-b4b8db0a845d?source=rss------module_federation-5>Building React Apps Faster with Rsbuild — My Journey Away from Webpack</a></td><td><code>react-microfrontend, webpack, module-federation, react, rsbuild</code></td></tr><tr><td><a target='_blank' href=https://medium.com/beer-and-servers-dont-mix/micro-frontend-strategy-choosing-between-shell-apps-and-independent-systems-2010a1eeec9a?source=rss------module_federation-5>Micro Frontend Strategy: Choosing Between Shell Apps and Independent Systems</a></td><td><code>mfe, module-federation, micro-front-end</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@307776572/in-2025-this-is-how-micro-frontends-should-be-done-14acc90fde35?source=rss------micro_frontends-5>In 2025, this is how Micro Frontends should be done:</a></td><td><code>micro-frontends, front-end-development</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@rithishjakkireddy/micro-frontends-with-react-vite-typescript-a-hands-on-guide-9005fee02d21?source=rss------module_federation-5>Micro Frontends with React, Vite &amp; TypeScript: A Hands-On Guide</a></td><td><code>module-federation, frontend-architecture, react, vites, implement-microfrontend</code></td></tr><tr><td><a target='_blank' href=https://medium.com/rethinking-the-client-a-new-era-of-modular/how-to-build-and-version-client-side-services-without-losing-your-mind-5fbd3c43535b?source=rss------micro_frontends-5>How to Build and Version Client-side Services &lpar;Without Losing Your Mind&rpar;</a></td><td><code>versioning-strategies, micro-frontends, modular-design, semantic-versioning, frontend-architecture</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@rivinsand/why-my-microfrontend-research-led-me-back-to-monoliths-05774bc1fe79?source=rss------micro_frontends-5>Why my microfrontend research led me back to monoliths</a></td><td><code>monolith, micro-frontends, software-architecture, module-federation, frontend-development</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@rivinsand/why-my-microfrontend-research-led-me-back-to-monoliths-05774bc1fe79?source=rss------module_federation-5>Why my microfrontend research led me back to monoliths</a></td><td><code>monolith, micro-frontends, software-architecture, module-federation, frontend-development</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@saranya.shanmugavel/import-maps-advanced-module-loading-made-simple-dacc6174405f?source=rss------micro_frontends-5>Import Maps: Advanced Module Loading Made Simple</a></td><td><code>webpack, micro-frontends, importmap, javascript</code></td></tr><tr><td><a target='_blank' href=https://mustafacagri.medium.com/cursor-ide-claude-sonnet-4-ger%C3%A7ek-bir-proje-deneyiminden-%C3%A7%C4%B1kar%C4%B1lan-dersler-b597d32d0b34?source=rss------micro_frontends-5>CURSOR IDE + Claude Sonnet 4: Gerçek Bir Proje Deneyiminden Çıkarılan Dersler</a></td><td><code>ai, cursor, sonnet, micro-frontends, claude</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@faruksekman/front-endde-%C3%B6l%C3%A7eklenebilir-mimari-angular-projelerinde-monorepo-micro-frontends-bd8acdfe7b75?source=rss------micro_frontends-5>Front-End’de Ölçeklenebilir Mimari: Angular Projelerinde Monorepo &amp; Micro Frontends</a></td><td><code>javascript, angular, micro-frontends, monorepo, frontend-architecture</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@matyas_53422/consuming-web-components-in-angular-and-react-micro-frontends-within-an-nx-ecosystem-0afa409e1399?source=rss------module_federation-5>Consuming Web Components in Angular and React Micro Frontends within an NX Ecosystem</a></td><td><code>react, nx, angular, module-federation, monorepo</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@vasanthancomrads/real-world-micro-frontends-with-module-federation-in-nx-monorepos-a-beginners-guide-with-bf24a5f60d38?source=rss------micro_frontends-5>Real-World Micro Frontends with Module Federation in Nx Monorepos: A Beginner’s Guide with…</a></td><td><code>angular, module-federation, micro-frontends, nx-monorepo, react</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@vasanthancomrads/real-world-micro-frontends-with-module-federation-in-nx-monorepos-a-beginners-guide-with-bf24a5f60d38?source=rss------module_federation-5>Real-World Micro Frontends with Module Federation in Nx Monorepos: A Beginner’s Guide with…</a></td><td><code>angular, module-federation, micro-frontends, nx-monorepo, react</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@matyas_53422/building-angular-and-react-microfrontends-with-module-federation-and-nx-703cd5118725?source=rss------micro_frontends-5>Building Angular and React Microfrontends with Module Federation and NX</a></td><td><code>module-federation, micro-frontends, nx, react, angular</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@matyas_53422/building-angular-and-react-microfrontends-with-module-federation-and-nx-703cd5118725?source=rss------module_federation-5>Building Angular and React Microfrontends with Module Federation and NX</a></td><td><code>module-federation, micro-frontends, nx, react, angular</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@madhanprasath.dev/seamless-integration-implementing-module-federation-to-use-vue-components-in-react-7164bb24ba02?source=rss------module_federation-5>Seamless Integration: Implementing Module Federation to Use Vue Components in React</a></td><td><code>module-federation, vuejs, reactjs</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@shrikantkale136_16701/angular-micro-frontends-getting-started-c8a698f29784?source=rss------micro_frontends-5>Angular — Micro-Frontends Getting started</a></td><td><code>angular-microfrontend, micro-frontends, angular, angular-architecture, module-federation</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@shrikantkale136_16701/angular-micro-frontends-getting-started-c8a698f29784?source=rss------module_federation-5>Angular — Micro-Frontends Getting started</a></td><td><code>angular-microfrontend, micro-frontends, angular, angular-architecture, module-federation</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@comehere1207/mastering-micro-frontend-architecture-a-production-ready-implementation-ea8991b677e9?source=rss------module_federation-5>Mastering Micro Frontend Architecture: A Production-Ready Implementation</a></td><td><code>react-microfrontend, micro-frontend-deployment, rspack, mfe, module-federation</code></td></tr><!-- BLOG-POST-LIST:END -->
</table>

<hr/>

### Connect with me on
<div id="badges">
  <a href="https://twitter.com/shindesan2012">
    <img src="https://img.shields.io/badge/shindesan2012-black?style=for-the-badge&logo=twitter&logoColor=white" alt="Twitter Badge"/>
  </a>
  <a href="https://www.linkedin.com/in/shindesantosh/">
    <img src="https://img.shields.io/badge/shindesantosh-blue?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn Badge"/>
  </a>
   <a href="https://blog.santoshshinde.com/">
    <img src="https://img.shields.io/badge/Blog-black?style=for-the-badge&logo=medium&logoColor=white" alt="Medium Badge"/>
  </a>
  <a href="https://www.buymeacoffee.com/santoshshin" target="_blank">
    <img src="https://img.shields.io/badge/buymeacoffee-black?style=for-the-badge&logo=buymeacoffee&logoColor=white" alt="Buy Me A Coffee"/>
  </a>
</div>
