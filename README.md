# frcbot
A Reddit bot to help out around the /r/FRC sub. It's hastily-thrown together and not nearly feature-complete, but it works for now.

##Requirement
- Python 2

##Setup
NOTE: This was developed and tested on a Linux (Debian) machine. YMMV with other distros/platforms. I also did not test these instructions from scratch. If anything is wrong, please submit a PR. If anything is horribly wrong, please head to your designated fallout bunker.

1. Clone this repo
2. Run `pip install -r requirements.txt`
3. Sign up for a [new Reddit account](https://www.reddit.com/login) for your bot (highly recommended)
4. Create and populate the `settings.cfg` file (see below)
5. Create a [Reddit developer app](https://www.reddit.com/prefs/apps/) and copy the values into a new `oauth.ini` file

##Configuration
####settings.cfg
The settings and values should look like these (substituting your own actual values)
```ini
[Reddit]
subreddit=frctest
useragent=platform:botname:v0.0.0 (by /u/username)

[TBA]
appid=username:botname:0.0.0
```

####oauth.ini
Fill in your Reddit application key and secret that you created earlier. Leave everything else as-is.
```ini
[app]
scope = edit,identity,modposts,read,submit
refreshable = True
app_key = YOUR_KEY_HERE
app_secret = YOUR_SECRET_HERE

[server]
server_mode = True
url = 127.0.0.1
port = 65010
redirect_path = authorize_callback
link_path = oauth
```

##Usage
Edit the script to change the title's week number. This behavior will change later. Then run `python weekly_discussion.py`. Keep in mind that the script only takes a few minutes at most to run and may require some input/interaction, so I would suggest **not** running it as a cron job or in the background for now.

On your first run, you will need to authenticate with Reddit OAuth by logging in to a URL printed in the console. It's a localhost address, so you'll need to perform this on the server. I used Debian's built-in **w3m** terminal browser (`w3m http://127.0.0.1/oauth`), other distros may have something similar. Once PRAW 4 is released, this should be a lot easier to configure.

Also, if your bot account is brand-spankin' new and/or does not have a verified email address, you will get hit with CAPTCHA requests everytime it attempts to post. The console will print out a URL that you need to visit (this can be from any computer) that has the image. Type the letters into the console, hit Enter and the script will continue as planned.
