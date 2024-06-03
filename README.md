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

#### Videos
1. [Micro-frontend Anti-patterns](https://www.youtube.com/watch?v=b9Zpi-oajA0)
2. [Micro-Frontends with Module Federation: Beyond the Basics](https://www.youtube.com/watch?v=tzXCrCwybgE)

#### Courses

1. [Microfrontends with React: A Complete Developer's Guide](https://www.udemy.com/course/microfrontend-course/learn/lecture/23206792#overview) by [Stephen Grider](https://www.linkedin.com/in/stephengrider)


### Recent Medium Posts

<table>
  <tr><th>Title</th><th>Categories</th></tr>
  <!-- BLOG-POST-LIST:START --><tr><td><a target='_blank' href=https://www.jimdoverse.com/strictly-typed-react-components-with-graphql-220365bde1bb?source=rss------micro_frontends-5>Strictly typed React components with GraphQL</a></td><td><code>typescript, typescript-with-react, micro-frontends, react, graphql</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@anjivarma.penmatsa/create-micro-frontends-using-react-and-module-federation-plugin-097e414fa411?source=rss------micro_frontends-5>Create Micro-Frontends using React and Module Federation Plugin</a></td><td><code>blog, webpack, javascript, react, micro-frontends</code></td></tr><tr><td><a target='_blank' href=https://amberfung.medium.com/micro-frontend-module-federation-setup-in-vite-71b323bd90a4?source=rss------micro_frontends-5>Micro-frontend — Module Federation Setup in Vite</a></td><td><code>micro-frontends, frontend-architecture, reactjs, react</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@nimithbbz10/microfrontend-how-to-access-the-routes-of-remote-projects-in-the-host-project-react-vite-0124859eac47?source=rss------micro_frontends-5>MicroFrontend : How to access the routes of Remote projects in the Host project &lpar; React + Vite &rpar;</a></td><td><code>vitejs, react-router-dom, reactjs, micro-frontends, react</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@soumyanildas/micro-frontend-setup-with-nx-rspack-module-federation-2-0-and-react-698674edb09f?source=rss------module_federation-5>Micro Frontend Setup with Nx, Rspack, Module Federation 2.0  and React</a></td><td><code>module-federation, frontend, rspack, nx, react</code></td></tr><tr><td><a target='_blank' href=https://kasata.medium.com/practical-guide-to-micro-frontend-architecture-ef8da2277b67?source=rss------micro_frontends-5>Practical Guide to Micro-Frontend Architecture</a></td><td><code>modern-web-techniques, micro-frontends, web-development, scalable-web-apps, frontend-architecture</code></td></tr><tr><td><a target='_blank' href=https://medium.com/front-end-weekly/introduction-to-micro-frontends-94055e77eaa4?source=rss------micro_frontends-5>Introduction to Micro Frontends</a></td><td><code>micro-frontends, micro-front-end, implement-microfrontend, react-microfrontend, what-is-micro-frontend</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@p.aditya.198/micro-frontends-using-module-federation-93633641622d?source=rss------module_federation-5>Micro Frontends using module federation.</a></td><td><code>implement-microfrontend, webpack, react, module-federation</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@ravisharma50063/a-comprehensive-guide-to-micro-frontend-development-benefits-terminology-and-best-practices-5e61511736dc?source=rss------micro_frontends-5>A Comprehensive Guide to Micro Frontend Development: Benefits, Terminology, and Best Practices</a></td><td><code>scalability, flexibility, micro-frontends, web-development</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@hurkanugur/a-guide-to-module-federation-and-micro-frontend-applications-in-angular-part-2-dc9bc5472782?source=rss------micro_frontends-5>A Guide to Module Federation and Micro-Frontend Applications in Angular — Part 2</a></td><td><code>standalone-component, angular, module-federation, micro-frontends, webpack-5</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@hurkanugur/a-guide-to-module-federation-and-micro-frontend-applications-in-angular-part-2-dc9bc5472782?source=rss------module_federation-5>A Guide to Module Federation and Micro-Frontend Applications in Angular — Part 2</a></td><td><code>standalone-component, angular, module-federation, micro-frontends, webpack-5</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@hurkanugur/a-guide-to-module-federation-and-micro-frontend-applications-in-angular-part-1-1ec0a62191b5?source=rss------micro_frontends-5>A Guide to Module Federation and Micro-Frontend Applications in Angular — Part 1</a></td><td><code>webpack-5, standalone-component, angular, micro-frontends, module-federation</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@hurkanugur/a-guide-to-module-federation-and-micro-frontend-applications-in-angular-part-1-1ec0a62191b5?source=rss------module_federation-5>A Guide to Module Federation and Micro-Frontend Applications in Angular — Part 1</a></td><td><code>webpack-5, standalone-component, angular, micro-frontends, module-federation</code></td></tr><tr><td><a target='_blank' href=https://amberfung.medium.com/micro-frontend-first-glance-af70b703e3ea?source=rss------micro_frontends-5>Micro-frontend — First Glance</a></td><td><code>frontend-architecture, micro-frontends, react, reactjs</code></td></tr><tr><td><a target='_blank' href=https://medium.com/flux-it-thoughts/micro-frontends-el-futuro-del-desarrollo-web-moderno-c9ae0d01702b?source=rss------module_federation-5>Micro-frontends: El futuro del desarrollo web moderno</a></td><td><code>technology, react, micro-frontends, module-federation, español</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@sameervaghela21/failed-to-construct-htmlelement-please-use-the-new-operator-this-dom-object-constructor-d726c5274683?source=rss------module_federation-5>Failed to construct ‘HTMLElement’: Please use the ‘new’ operator, this DOM object constructor…</a></td><td><code>webpack, module-federation, reactjs</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@lester.sconyers/dynamic-module-federation-with-vite-0bce2bfcc517?source=rss------module_federation-5>Dynamic Module Federation with Vite</a></td><td><code>module-federation, vitejs, ab-testing, react</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@mattia.darge/discover-the-power-of-microfrontends-a-revolution-in-frontend-development-76d94d8e88d2?source=rss------module_federation-5>Discover the power of microfrontends: A revolution in frontend development</a></td><td><code>frontend-architecture, module-federation, web-components, frontend, implement-microfrontend</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@avicsebooks/webpack-modulefedration-b4c50365380b?source=rss------module_federation-5>Webpack ModuleFedration</a></td><td><code>webpack-5, module-federation, implement-microfrontend</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@sarathdixit29/implementing-module-federation-in-next-js-with-typescript-and-eslint-ba6627a0686f?source=rss------module_federation-5>Implementing Module Federation in Next.js with TypeScript and ESLint</a></td><td><code>typescript, nextjs, webpack, module-federation</code></td></tr><!-- BLOG-POST-LIST:END -->
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
