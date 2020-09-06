---
title: "Github Codespaces"
date: 2020-09-06T08:33:01+02:00
draft: false
author: Tommaso Pifferi
tags:
  - github
  - codespaces
  - docker
  - devtools
---

After applying in June, I've finally been admitted to the beta of [Github Codespaces](https://github.com/features/codespaces) 🚀

At first I thought it was just a remote instance of VSCode, where you could open repos and have a peek at the code on the fly, without filling your hard drive with countless repos that you would never open a second time.

However, Codespaces are much more than that. A Codespace is basically a **stateful VM with root access**, with a base images that comes with `apt` preinstalled and that supports the major programming languages, and an instance of VSCode as the main form of interaction with the machine. You have a **terminal**! And you can **expose ports on the Internet** too!

## Features

It offers many customizations out of the box:

- you can override the base image of the VM by creating a `.devcontainers` folder with a `Dockerfile` inside. Microsoft has already [created many containers](https://github.com/microsoft/vscode-dev-containers/tree/master/containers) for you to try
- you can bring all the extensions you use daily in `VSCode` in the VM by using a `devcontainer.json` file
- you can bring all your VSCode settings as well by committing a `.vscode/settings.json` file
- you can bring all your shell shortcuts, aliases and settings since a Codespace reads your `dotfiles` repo on startup
- you can connect to your Codespace from your local VSCode instance (although it requires a Microsoft account...)

I think Codespaces are a total game changer, especially for new developers that want to approach a new language and find a project to start experimenting, but:

- they are not confident with Docker
- they do not have a local dev environment for said language
- live in a place where Internet access is slow and/or metered, and they can't afford to download dependencies and setup a developer environment

## A walled garden?

I've heard complaints from many people when Github announced Codespaces back in June, especially regarding the fact that you did not code on your machine anymore, that coding in the browser moves people away from their physical computers, and so on. Furthermore, on Codespaces your coding experience is restricted to a closed-source environment controlled by Github, and once your tied to it you can't go back anymore.

I can't disagree more. A Codespace is basically a VM with a careful orchestration of software that allows you to develop in many programming languages, and a remote installation of VSCode. The base `Dockerfile` is [open source](https://github.com/microsoft/vscode-dev-containers/tree/master/containers/codespaces-linux), and you can use whatever base image you like, as I said above. VSCode is [open source](https://github.com/Microsoft/vscode), and there are [forks](https://github.com/VSCodium/vscodium) available and up-to-date. All the Codespace configuration files are in a format that is well-known and not proprietary: `Dockerfile` format, VSCode [`settings.json`](https://code.visualstudio.com/docs/getstarted/settings) and [`devcontainer.json`](https://code.visualstudio.com/docs/remote/devcontainerjson-reference) formats.

That's all. _If/When_ Github decides to change plans with Codespaces, like removing the free plan or start doing evil things, people can just push their changes and keep coding on their local machines, with no downtime at all.

I think Codespaces are actually an awesome competitor to other cloud-coding platforms that promoted walled gardens of some kind, and I look for more features as Codespaces come out of the beta phase
