## poly-on-fire-fb-messenger-bot

Facebook Messenger chat bot code deployed to Firebase, barely if at all even relevant to Polymer.

I do have mine running on a polymer app, and especially
the rewrite code below does help you figure out how to do functions and a
single page app on the same firebase host, but otherwise this is mostly all
a nodeJs app as code is shown on this project

## From this video ##

Most of this code was taken directly from this video, except obviously the nodeJs setup on firebase

* https://www.youtube.com/watch?v=bUwiKFTvmDQ&t=796s

How to do the facebook side is covered pretty well in this video, starting around 11:30 minutes

## NodeJS setup on Firebase ##

Mostly from first 5 minutes of this video

* https://youtu.be/LOeioOKUKI8

## Verify from bash shell ##

`curl -X GET "https://<mydeployedsite>/webhook?hub.verify_token=<mychallengetoken>&hub.challenge=CHALLENGE_ACCEPTED&hub.mode=subscribe"`

## Re-Write necessary: ##

* In firebase.json there is a rewrite which you would need to be able to make the webhook nodeJs function work on a page that is otherwise single page app.

* It is only a co-incidence that I got this to work from experimentation. Mainly the rewrite has to be in order of the ** last! Your single page app
won't work if ** is first!

## Access Code ##
You will also need this line to put in your access code from the bash shell:

`firebase functions:config:set pmpageaccesstoken.key="PM_PAGE_ACCESS_TOKEN" pmpageaccesstoken.id="<access token>"`

This is the code in index.js that get's that value back out:
* `functions.config().pmpageaccesstoken.id `

This is the url to learn more about how to use env variables in firebase functions:
* https://firebase.google.com/docs/functions/config-env

You could obviously hard code the access code straight in the index.js,
but that doesn't apply to me because it's public on github :) where you're reading it now.

## General Experience Notes ##

Everything went pretty nearly like the videos show, except I spent a lot of time doing this on various objects to learn how to parse the messages from facebook:

* `console.log("SOME MESSAGE: \n "+stringify(req.body));`
