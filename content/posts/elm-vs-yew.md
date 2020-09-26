---
title: "Elm vs Yew"
date: 2020-09-23T21:50:28+02:00
draft: false
author: Tommaso Pifferi
tags:
  - elm
  - yew
  - rust
  - frontend
  - wasm
---

_A live demo for this post can be found [here](/experiments/elm-vs-yew)._

---

Recently I've been playing with [Yew](https://yew.rs/), a web framework written in Rust that compiles to WebAssembly. It borrows the [Elm](https://elm-lang.org/) model (`model`, `view`, `update`) and adds a JSX-like syntax on top of it. At first I was leaning to another framework, [Seed](https://seed-rs.org/), that is literally Elm in Rust if you have a quick look at the syntax, but I ended up with Yew. While they are both amazing, Yew seemed a bit more mature to me (although a bit lacking in documentation) and the JSX syntax is a big selling point.

I am no expert in Rust or WASM, but I was sure that something that compiles to WASM would have a huge performance boost with respect to traditional apps written in (or compiled to) Javascript. So I tried to create a canvas-like interface with some kind of animation that followed the mouse pointer, using WASM instead of pure CSS or something in the like. I started with a grid of `<div>`, each one with an attached event handler that toggled a class on `mousenter`/`mouseleave`. As I played with it, I was baffled by how slow the framework applied the class as I moved the pointer over the grid. I couldn't believe it: the model was embarrassingly simple, I was not passing around big objects by copy, the view' elements were properly keyed. What now?

Since I did not know if it was a problem regarding my (probably horrible) implementation, I decided to port the exact same project to Elm and check the result. It was amazingly fast and responsive, just as I expected the Yew app to be. At this point I decided to postpone playing with Yew and created an app that compares the two implementations, and it works as some kind of visual benchmark. You can check it out [here](/experiments/elm-vs-yew).

If you spot the performance issues in the Yew app, please open an issue in [the repo](https://github.com/neslinesli93/elm-vs-yew). I will be more than happy to fix it, and give Yew the justice it deserves :)
