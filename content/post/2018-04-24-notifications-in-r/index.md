---
title: "Getting system notifications with R"
subtitle: ""
summary: "Summary"
authors: [admin]

tags: [linux,r,programming]
categories: [data-science,tech]
projects: []

date: "2018-04-24T00:00:00Z"
lastmod: "2018-04-24T00:00:00Z"
featured: false
draft: false

image:
  caption: ""
  focal_point: ""
  preview_only: true
---

So today I was making quite time consuming simulations in R, and I was wondering if there was a way to know when the simulations were finished so I could have a look at the results. Relevant xkcd:

{{< figure src="https://imgs.xkcd.com/comics/compiling.png" title="[xkcd 303](https://xkcd.com/303/)" >}}

For those familiar with bash scripting in Linux, you can use `notify-send` to, well, send desktop notifications using the `libnotify` library. For those familiar with R, you may also know that R can directly execute system commands using the `system()` function.

Having this in mind, the answer to my problem was just creating a function that
 - can execute any[^fn1] R call
 - prints the elapsed time to execute it
 - sends a permanent desktop notification
 - emits a *completion* alert sound[^fn2]

*Of course*, I decided to call the function `lok_regar()`:
```r
lok_regar <- function(call) {
  print(system.time(call))
  system("notify-send -i rstudio -u critical 'Finished calculations' 'Get back to work!'")
  system("paplay /usr/share/sounds/freedesktop/stereo/complete.oga")
}
```

I'm not sure this function is the most elegant way to do this, but it's pretty easy to use and does its job, and it looks pretty:

{{< figure src="r-notify.png" title="System notification on GNU/Linux" >}}

In the future I would like to print the elapsed time into the notification itself, but I'm not quite sure it's possible.

[^fn1]: Well, probably not any, but it works in the scenarios I've tested it.
[^fn2]: It doesn't always work, I don't know why.

