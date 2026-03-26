---
title: "How NPM broke my server"
date: 2024-10-20
tags: ["linux", "tech", "pnpm", "hosting"]
description: "NPM ate all the RAM on my 1GB droplet. pnpm saved the day."
---

I own a small **1vCPU** and **1GB** RAM Digital Ocean Droplet. Which costs me around 500rs per month.

Last week I was trying to build a Documentation website with [Docusaurus](https://docusaurus.io/) for a project. I pushed the project to GitHub and cloned it to my server.

Then I started installing with npm. I ran `npm install` and it started installing the dependencies. After a few minutes, I got an error saying that the server is out of memory. I was surprised because I have only 1GB of RAM and the server was not doing anything else. The CPU and Disk usage was very high.

I checked the memory usage with `htop`. But I couldn't figure it out because the server was unresponsive. I had to reboot the server to get it back online.

I tried to install the dependencies again, but the same thing happened. I was frustrated and started searching for the issue. I found that npm uses a lot of memory to install the dependencies. I tried to increase the swap memory, but it didn't help.

Then I was fed up using npm and according to a few reddit posts they mentioned that `pnpm` is a good alternative. So I installed pnpm with `npm install -g pnpm`. It worked and I tried to install the dependencies with `pnpm install`. It worked like a charm.

## Reason behind the issue

- NPM installs dependencies in a flat structure. So if a package is used in multiple dependencies, it will be installed multiple times.
- NPM uses a lot of memory to install dependencies. So if you have a small server, it will run out of memory.
- NPM uses a lot of disk space. If you have limited disk space, it will run out.

## Conclusion

- If you have a small server, use `pnpm` instead of `npm`.
- If you have a large server, `npm` works fine.
- If you want to save disk space, `yarn` or `pnpm` are good alternatives.

### Links

- [pnpm](https://pnpm.io/)
- [Docusaurus](https://docusaurus.io/)
- [Digital Ocean](https://www.digitalocean.com)
