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
  <!-- BLOG-POST-LIST:START --><tr><td><a target='_blank' href=https://medium.com/@krativarshney7/angular-and-micro-frontends-6d6832702ae4?source=rss------micro_frontends-5>Angular and Micro Frontends</a></td><td><code>micro-frontends, programming, technology, software-architecture, angular</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@parthpatel1207/building-focused-uis-how-micro-frontends-are-evolving-90fd17ba193a?source=rss------module_federation-5>Building Focused UIs: How Micro Frontends Are Evolving</a></td><td><code>monorepo-strategies, module-federation, micro-frontend-tips, modular-ui-design, storybook-components</code></td></tr><tr><td><a target='_blank' href=https://tech.groww.in/from-zero-to-mfe-building-the-system-and-the-developer-experience-b8a07e873932?source=rss------micro_frontends-5>From Zero to MFE — Building the System &lpar;and the Developer Experience&rpar;</a></td><td><code>monolithic-architecture, micro-frontends, backend</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@dgupta.jit/mastering-the-monorepo-why-it-matters-in-a-micro-frontend-world-1312fbc130c8?source=rss------micro_frontends-5>Mastering the Monorepo: Why It Matters in a Micro Frontend World</a></td><td><code>angular, micro-frontends, nx, monorepo, javascript</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@akhshyganesh/how-we-hosted-a-vue-2-and-vue-3-family-reunion-aka-mfe-with-module-federation-104f5b30e294?source=rss------module_federation-5>How We Hosted a Vue 2 and Vue 3 Family Reunion &lpar;aka MFE with Module Federation&rpar;</a></td><td><code>vuejs, akhshyganesh, microservices, module-federation, legacy</code></td></tr><tr><td><a target='_blank' href=https://tech.groww.in/why-we-broke-the-monolith-microfrontends-at-scale-part-1-3b6553b0a6c3?source=rss------micro_frontends-5>Why We Broke the Monolith — Microfrontends at Scale &lpar;Part 1&rpar;</a></td><td><code>monolithic-architecture, backend, micro-frontends</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@hemanthkumarrajan/building-a-microfrontend-architecture-with-react-vue-angular-and-next-js-in-an-angular-host-72753562c338?source=rss------module_federation-5>Building a Microfrontend Architecture with React, Vue, Angular, and Next.js in an Angular Host</a></td><td><code>react-vue-integration, frontend-architecture, angular, micro-front-end, module-federation</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@MastersTechie/micro-frontend-using-webpack-module-federation-ep4-ba7f9b44aed9?source=rss------module_federation-5>Micro-frontend using Webpack Module Federation — EP4</a></td><td><code>module-federation, react, backend-development, frontend-development, micro-front-end</code></td></tr><tr><td><a target='_blank' href=https://engineering.dunelm.com/micro-frontends-the-story-so-far-758b597ce7a8?source=rss------micro_frontends-5>Micro Frontends — The Story So Far</a></td><td><code>micro-frontends, technology, digital-transformation, web-development</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@DaveLumAI/micro-frontends-like-a-software-potluck-but-with-less-tupperware-65cb0121404f?source=rss------micro_frontends-5>Micro Frontends: Like a Software Potluck, But With Less Tupperware</a></td><td><code>micro-frontends, architecture-series, episode-7, ai-art, architecture</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@pf.souza15/why-modern-angular-projects-should-embrace-nx-dev-module-federation-a-real-world-perspective-f8beea7a39a5?source=rss------module_federation-5>Why Modern Angular Projects Should Embrace Nx.dev + Module Federation — A Real-World Perspective</a></td><td><code>nx, micro-front-end, typescript, angular, module-federation</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@pf.souza15/por-que-projetos-angular-devem-considerar-nx-dev-module-federation-hoje-mesmo-fea551ac86e7?source=rss------module_federation-5>Por que Projetos Angular Devem Considerar Nx.dev + Module Federation Hoje Mesmo</a></td><td><code>typescript, nx, module-federation, angualr, micro-frontend-deployment</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@elvinahmadov0/microfrontend-architecture-with-vite-module-federation-2e57cb144daa?source=rss------module_federation-5>Microfrontend Architecture with Vite + Module Federation</a></td><td><code>typescript, module-federation, zustand, react, react-microfrontend</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@ahmedoumezzine/construire-une-application-de-blog-avec-micro-frontends-un-guide-pratique-6e099d0f2959?source=rss------micro_frontends-5>Construire une Application de Blog avec Micro-Frontends : Un Guide Pratique</a></td><td><code>implement-microfrontend, react-micro-frontends, webpack-module-federation, micro-frontend-deployment, micro-frontends</code></td></tr><tr><td><a target='_blank' href=https://2fik.medium.com/microfrontend-og-domeneeierskap-fordeler-og-ulemper-2909131b8018?source=rss------micro_frontends-5>Microfrontend og domeneeierskap: Fordeler og ulemper</a></td><td><code>micro-frontends, micro-frontend-deployment, teamledelse, domain-driven-development, produktledelse</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@sankalppolk123/-4033cc843591?source=rss------module_federation-5>.</a></td><td><code>javascript, microservices, micro-front-end, modern-js, module-federation</code></td></tr><tr><td><a target='_blank' href=https://medium.com/flux-it-thoughts/micro-frontends-how-do-monorepos-work-e36778f8a4d2?source=rss------micro_frontends-5>Micro-Frontends: How do Monorepos Work?</a></td><td><code>monorepo, english, technology, micro-frontends</code></td></tr><tr><td><a target='_blank' href=https://medium.com/flux-it-thoughts/micro-frontends-c%C3%B3mo-funcionan-los-monorepos-2c4883ec902b?source=rss------micro_frontends-5>Micro-frontends: ¿Cómo funcionan los monorepos?</a></td><td><code>technology, español, micro-frontends, monorepo</code></td></tr><tr><td><a target='_blank' href=https://medium.com/@werlitoncarlos/parte-3-enviando-dados-entre-aplica%C3%A7%C3%B5es-com-module-federation-42d9abc096a4?source=rss------module_federation-5>[Parte 3] Enviando dados entre aplicações com Module Federation</a></td><td><code>react, front-end-development, module-federation, javascript</code></td></tr><tr><td><a target='_blank' href=https://sagarsnath.medium.com/unleashing-the-power-of-webpack-the-unsung-hero-of-modern-web-development-and-the-backbone-of-0cae95a75a32?source=rss------module_federation-5>Unleashing the Power of Webpack: The Unsung Hero of Modern Web Development and the Backbone of…</a></td><td><code>web-development, webpack, module-federation, javascript, angular</code></td></tr><!-- BLOG-POST-LIST:END -->
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
