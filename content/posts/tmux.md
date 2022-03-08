---
title: "How to Go and Grab a Coffee while Keeping Your Vim Running on CLAC"
date: 2021-12-02T12:30:14-05:00
draft: false

tags: ["Advanced Programming"]
categories: ["Handy Tools"]
author: Tianqi Zhao
showToc: true
TocOpen: true
---

While taking the Advanced Programming class, the thing that bothers me the most is not that we need to program using Vim in CLAC, a remote server, but every time when I leave for a cup of coffee, my laptop sleeps, and CLAC connection is automatically closed, so I have to type `clac`, `cd cs3157/labN/part1`, `vim xxx.c` again and again, which is really annoying.

Jae briefly mentioned a handy tool, called `tmux`, in listserv, and I found that is useful if you are a coffee person like me.

# What is `tmux`?

In short, tmux is a *terminal multiplexer* tool that allows you to run multiple terminal programs in the background. You can detach a session (let's say, `vim lab3.c`) when you want to leave, and re-attach it at any time. 

There are so many things behind tmux that will are useful for development, but here I will just go through a very simple case: **how to keep your vim process running on CLAC and go and grab a coffee**.

# Keep a Session Running in the Background

Now, logging in to CLAC by either typing `clac` (a shortcut that is introduced in listserv) or doing it in the normal way.

```bash
clac
```

Let's create a new tmux session by typing:

```bash
tmux new
```

Now, you are entering to a new tmux session. Type `tmux ls` to see all active tmux sessions.

```bash
test@clac:~$ tmux ls
0: 1 windows (created Thu Dec  2 11:27:27 2021) [28x40] (attached)
```

For now, You can just do all the things that you normally would do in CLAC, such as `cd cs3157/labN/partN`, `vim hello.c`, etc.

When you're about to leave, use key binding `C-b d`.

> `C` here means `Control`/ `Command`.

You will now see your terminal has been split into two. The left session is the vim session that you were running, and the right session is a brand new session.

You can now safely leave, get a coffee, have a rest, or even close the terminal, and when you come back and would like to restart, type:

```bash
clac
tmux attach
```

You will see that you have retrieved the session you were running before. Good luck on coding!

When you have submitted the lab and want to sleep, just type `exit` to exit the tmux session.

> tmux will also be useful if you want to split your windows into two, one at the current lab and the other at the previous lab solutions.

# Useful Links

If you'd like to know more about tmux, here are two links that might be useful:

[tmux Official Document: Getting Started](https://github.com/tmux/tmux/wiki/Getting-Started)

[A Quick and Easy Guide to tmux](https://www.hamvocke.com/blog/a-quick-and-easy-guide-to-tmux/)