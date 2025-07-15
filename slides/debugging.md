---
title: "Debugging Your Code"
subtitle: "CIS 241, Dr. Ladd"
author: "`spacebar` to go to the next slide, `esc`/menu to navigate"
format:
  revealjs:
    theme: moon
    controls: true
    slide-level: 2
    transition: slide
    incremental: true
    center: true
    navigation-mode: vertical
    embed-resources: true
    self-contained-math: true
---

# Errors in Your Code Can Be Frustrating! 

## But here are some steps to try:

![](img/ladybug.jpg)

## Step 1: Define the Problem

Think about what you were *trying* to do vs. what happened instead. Create a hypothesis for what went wrong.

## Step 2: Read the Error Message.

Look for a line number where the error is occurring.

Sometimes the bug is in the line *before* the one that threw the error!

## Step 3: Re-run code from the beginning.

Sometimes you ran something out of order. Go back to the beginning of your code and re-run to see if that will fix it.

## Step 4: Talk it out!

Try your best to explain the problem *out loud*, preferably to a friend or teammate.

Practice [rubber duck debugging](https://en.wikipedia.org/wiki/Rubber_duck_debugging).

![](img/rubberduck.png)

## Step 5: Check instructions, documentation, and Google.

If you're lost, refer to all the resources you have: cheatsheets, lab guides, online documentation. Don't forget [RAD CAT](https://jrladd.com/CIS241/radcat)!

And when in doubt: Google the error message and see if someone else had the same problem!

## Step 6: Ask for help!

Don't let a single bug frustrate you for too long. If none of the above strategies worked, ask a classmate, PAL tutor, or instructor for help with the problem.

# Avoid Bugs before they happen!

## Save and/or "Restart and Run All" Often.

If you're getting the same bug repeatedly in the same cell despite making changes, it could be that something is "stuck" in memory. Use the "restart and run all" button to try it again with a fresh kernel.

## Use good names.

Name your variables and dataframes with care. Rename things to make them more clear. Good names can help you find a problem quickly.

## Start simple, and build up little by little.

Don't try to write a whole program all in one go.

## Run your code line-by-line.

Check that it works *as you go*.

## Leave yourself good annotations and comments!

Use `#` to leave comments: remind yourself what certain lines of code are doing.

