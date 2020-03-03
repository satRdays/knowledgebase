---
date: 2016-10-24T21:07:13+01:00
title: Technology
weight: 50
---


## Working together
We use Slack and Github as our primary tools to work as a group. Join us on the #satrdays-chat channel on the [R User Groups Slack](https://join.slack.com/t/rusergroups/shared_invite/enQtMjEyNDA3MzcyMjczLTE3NWEzNjQ3MjZiMWM0OGE2ZWFiZDliNTY4NTJjYWY1NGNjMmNlNDUzNzkzOTZmMDBjYjRiZjFhNjk4MDY0ZGY) to chat.

## Ticketing
We have a specific account for Tito that charges 1% commission on tickets due to the community, non-profit nature of the events. Use the slack channel to request access from Dave Parr.

[Eventbrite](https://www.eventbrite.com/), [Tito](https://ti.to/) and [Ticket Tailor](https://www.tickettailor.com/) have all been used for events in the past.

## Marketing
Most event organisers use [Mailchimp](//mailchimp.com) to build a mailing list of attendees and communicate with them. We have LinkedIn and Twitter central accounts that organisers can be granted access for the run up to the events and during their events.

## Call for Papers
We have an ongoing discount with [sessionize.com](//sessionize.com) and will support the use of this with the remaining R Consortium funds for folks to use for their CFPs.

## Websites
We have built a set of partials for [Hugo](//gohugo.io) which are designed as a quick start solution for each events individual website. They are hosted on [GitHub](https://github.com/satRdays/satRday_site_template) along with guidance on their use.

Most of our websites are [Hugo](//gohugo.io) or [Jekyll](//jekyllrb.com) and are deployed on [Netlify](//netlify.com). Netlify kindly support us by hosting us on their open source plan.

Every events naming follows a convention `[city][YYYY]` on github and netlify. This means you can find the github repo at `github.com/satrdays/[city][YYYY]` and the deploy logs for debugging and monitoring at `app.netlify.com/sites/[city][YYYY]`

### Troubleshooting

### Cache expiry
If you get a problem like
> 5:09:31 PM: Error fetching branch: https://x-access-token:v1.c95a3f12816ae98874294b4968b94a01d15550e3@github.com/satRdays/kampala2019 refs/heads/master

Perform a retry with a clear cache in netlify - some stuff in the cache expired and you need to basically give it a refresh

### Submodule pains
If you see problems like 
> 5:01:03 PM: Error checking out submodules: Submodule 'themes/hugo-agency-theme' (https://github.com/digitalcraftsman/hugo-agency-theme) registered for path 'themes/hugo-agency-theme'
> Submodule 'themes/hugo-satrdays-theme' (https://github.com/satRdays/hugo-satrdays-theme) registered for path 'themes/hugo-satrdays-theme'
> Cloning into '/opt/build/repo/themes/hugo-agency-theme'...
> Cloning into '/opt/build/repo/themes/hugo-satrdays-theme'...
> error: Server does not allow request for unadvertised object 6c9d08341eedd557bc856979d4d894f30672bbdc
> Fetched in submodule path 'themes/hugo-agency-theme', but it did not contain 6c9d08341eedd557bc856979d4d894f30672bbdc. Direct fetching of that commit failed.

The issue is that you committed something to a submodule, and committed that submodule update to your repo, but you *didn't* push the commit in the submodule. It's looking for a commit that doesn't exist. In the case of the satRdays you generally shouldn't be doing anything in the submodules so in a situation like this you need to reset the submodule in question to a point that's online using:
```
cd themes/hugo-agency-theme
git checkout commitsha
cd ..\..
git add themes/hugo-agency-theme
git commit -m "submodule reset"
git push
```

