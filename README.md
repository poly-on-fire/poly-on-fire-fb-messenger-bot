## poly-on-fire-fb-messenger-bot

Facebook Messenger chat bot code deployed to Firebase, barely if at all even relevant to Polymer


## From this video ##

Most of this code was taken directly from this video, except obviously the nodeJs setup on firebase

* https://www.youtube.com/watch?v=bUwiKFTvmDQ&t=796s

## NodeJS setup on Firebase ##

Mostly from first 5 minutes of this video

* https://youtu.be/LOeioOKUKI8

## Verify from bash shell ##

`curl -X GET "https://<mydeployedsite>/webhook?hub.verify_token=<mychallengetoken>&hub.challenge=CHALLENGE_ACCEPTED&hub.mode=subscribe"`

## Re-Write necessary: ##

* In firebase.json there is a rewrite which you would need to be able to make the webhook nodeJs function work on a page that is otherwise single page app

## Access Code ##
You will also need this line to put in your access code from the bash shell:

`firebase functions:config:set pmpageaccesstoken.key="PM_PAGE_ACCESS_TOKEN" pmpageaccesstoken.id="<access token>"`

This is the code in index.js that get's that value back out:
* `functions.config().pmpageaccesstoken.id `

This is the url to learn more about how to use env variables in firebase functions:
* https://firebase.google.com/docs/functions/config-env

## General Experience Notes ##

Everything went pretty nearly like the videos show, except I spent a lot of time doing this on various objects to learn how to parse the messages from facebook:

* `console.log("SOME MESSAGE: \n "+stringify(req.body));`
