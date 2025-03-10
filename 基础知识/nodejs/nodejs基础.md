## 什么是node

简单地说 Node.js 就是运行在服务端的 JavaScript。是一个基于Chrome JavaScript 运行时建立的一个平台。

Node.js是一个事件驱动I/O服务端JavaScript环境，基于Google的V8引擎，V8引擎执行Javascript的速度非常快，性能非常好。

## 为什么会出现node

有个叫Ryan Dahl的歪果仁，他的工作是用C/C++写高性能Web服务。对于高性能，异步IO、事件驱动是基本原则，但是用C/C++写就太痛苦了。于是这位仁兄开始设想用高级语言开发Web服务。他评估了很多种高级语言，发现很多语言虽然同时提供了同步IO和异步IO，但是开发人员一旦用了同步IO，他们就再也懒得写异步IO了，所以，最终，Ryan瞄向了JavaScript。因为JavaScript是单线程执行，根本不能进行同步IO操作，所以，JavaScript的这一“缺陷”导致了它只能使用异步IO。选定了开发语言，还要有运行时引擎。这位仁兄曾考虑过自己写一个，不过明智地放弃了，因为V8就是开源的JavaScript引擎。让Google投资去优化V8，咱只负责改造一下拿来用，还不用付钱，这个买卖很划算。于是在2009年，Ryan正式推出了基于JavaScript语言和V8引擎的开源Web服务器项目，命名为Node.js。虽然名字很土，但是，Node第一次把JavaScript带入到后端服务器开发，加上世界上已经有无数的JavaScript开发人员，所以Node一下子就火了起来。在Node上运行的JavaScript相比其他后端开发语言有何优势？最大的优势是借助JavaScript天生的事件驱动机制加V8高性能引擎，使编写高性能Web服务轻而易举。其次，JavaScript语言本身是完善的函数式语言，在前端开发时，开发人员往往写得比较随意，让人感觉JavaScript就是个“玩具语言”。但是，在Node环境下，通过模块化的JavaScript代码，加上函数式编程，并且无需考虑浏览器兼容性问题，直接使用最新的ECMAScript 6标准，可以完全满足工程上的需求。

## node的特点

作为后端JavaScript的运行平台，Node保留了前端浏览器JavaScript中那些熟悉的接口，没有改写语言本身的任何特性， 依旧基于作用域和原型链， 区别在于它将前端中广泛运用的思想迁移到了服务器端。下面我们来看看Node相较其他语言的一些特点。

### 异步I/O

在Node中，绝大多数的操作都以异步的方式进行调用。在Node中，我们可以从语言层面很自然地进行并行I/O操作。每个调用之间无须等待之前的I/O调用结束。在编程模型上可以极大提升效率。

### 事件与回调函数

下面的例子展示的是Ajax异步提交的服务器端处理过程。Node创建一个Web服务器，并侦听8080端口。对于服务器，我们为其绑定了request事件，对于请求对象，我们为其绑定了data事件和end事件：
![[image (15).png]]

### 单线程

单线程的最大好处是不用像多线程编程那样处处在意状态的同步问题， 这里没有死锁的存在，也没有线程上下文交换所带来的性能上的开销。

单线程的弱点具体有以下3方面。

 无法利用多核CPU。

 错误会引起整个应用退出，应用的健壮性值得考验。

 大量计算占用CPU导致无法继续调用异步I/O。

Node采用了与Web Workers相同的思路来解决单线程中大计算量的问题：child_process。

子进程的出现，意味着Node可以从容地应对单线程在健壮性和无法利用多核CPU方面的问题。通过将计算分发到各个子进程，可以将大量计算分解掉，然后再通过进程之间的事件消息来传递结果，这可以很好地保持应用模型的简单和低依赖。通过Master-Worker的管理方式，也可以很好地管理各个工作进程，以达到更高的健壮性。

### 跨平台
![[image (16).png]]


## 适用场景

- Node擅长I/O密集型的应用场景基本上是没人反对的。 Node面向网络且擅长并行I/O， 能够有效地组织起更多的硬件资源，从而提供更多好的服务。 I/O密集的优势主要在于Node利用事件循环的处理能力，而不是启动每一个线程为每一个请求服务，资源占用极少。
    
- 通过合理的调度也适用于cpu密集的情况。
    

## 优点

1、Node是基于事件驱动和无阻塞的，所以非常适合处理并发请求，因此构建在Node上的代理服务器相比其他技术实现（如Ruby）的服务器表现要好得多。

2、Node.可以让开发人员更好的组织代码，提升复用性。并且可以处理文件与数据库。

3、基于Javascript，普及门槛低，JavaScript相对其他的企业级编程语言来说也简单一些，这样前端程序员就可以很快上手利用Node做后端的设计。

## 缺点

1、不适合计算密集型应用；

2、不适合大内存的应用；

3、不适合大量同步的应用。