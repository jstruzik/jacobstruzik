---
layout: post
title: "The Judgement of Commodus"
excerpt: "A tool to validate Github pull requests through thumbs up emojis."
categories: Projects
tags: [GitHub, emoji, commodus]
date: 2015-01-02T15:00:00-05:00
comments: true
---

Does anyone remember that guy in Gladiator that everyone hated? You know, the guy with the snark face that issued the death of poor Maximus and his family.

# ![]({{ site.url }}/img/commodus/commodus.jpg)

Yeah, that guy. His name is Emperor Commodus (or some of you may just know him as actor Joaquin Phoenix).

One of his most notable scenes in the movie is when he spares the life of the protagonist, Maximus, in the gladiator coliseum with a hesistant thumbs up. Way back when, it was common practice called [_pollice verso_](http://en.wikipedia.org/wiki/Pollice_verso) among the people of Ancient Rome to determine the fate of a defeated gladitor.


# ![]({{ site.url }}/img/commodus/commodus_2.gif)

At [Robin Powered](https://robinpowered.com), although we're not fighting to the death in front of thousands, we came to the realization that we needed a tool that would determine the fate of a pull request before the final merge.

Most of our developers here make use of [git flow](https://github.com/nvie/gitflow) so we wanted a process that would ensure that incoming pull requests would undergo a thorough QA process. Our general rule of thumb (dat pun) is once a pull request gets a `:+1:` from two different developers, it has the green light to get merged into our development branch.

Even with this unwritten process sometimes problems would arise where a developer would overlook things or forget to check for new commits after already giving their approval. Thankfully after Github [introduced multiple status checks](https://github.com/blog/1935-see-results-from-all-pull-request-status-checks) as well as [organization level webhooks](https://github.com/blog/1933-introducing-organization-webhooks) I decided it was time to write up an app that would automate this process for us.

Meet [commodus](https://github.com/robinpowered/commodus), a Sinatra based, Heroku-ready application that ensures your pull requests have the 👍's before merging.

Commodus simply requires a Redis instance, a Github token with `repo` permissions, and a [Github webhook](https://developer.github.com/webhooks/) setup to report `pull_request` and `issue_comment` to the application.

Once the application is setup, simply open up a new pull request and the status check should look something like:

# ![]({{ site.url }}/img/commodus/Screen_Shot_2015_01_02_at_1_40_36_PM.png)

Then some generous soul(s) comes along and give you the 👍

# ![]({{ site.url }}/img/commodus/Screen_Shot_2015_01_02_at_1_42_25_PM.png)

Great success!

# ![]({{ site.url }}/img/commodus/Screen_Shot_2015_01_02_at_1_42_30_PM.png)

Commodus also takes into account the 👎 as well! So if someone thinks your code sucks, they can let commodus know!

Check out the code [over at Github](https://github.com/robinpowered/commodus) for installation and setup instructions.