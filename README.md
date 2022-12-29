# Stereo Telegram Posts Printing Press

## What is it

It is a tool for creating specific posts for my Telegram [channel](https://t.me/stereobyavolkov) with stereo photos.

## Solved problems
I post stereo pairs as messages with grouped jpeg files and a description under the files. [An example of the post](https://t.me/stereobyavolkov/83) looks like this:

<img src="./docs/post-example.png" width="350" alt="post example" />

These posts have some features:
1. The description under the list of files
2. Link to anaglyphs

Let's consider each feature.

### The description under the list of files

It is a matter to post a few files in one post to avoid users annoying due to notifications flood. And this is the problem with posting it manually. The description can be attached to the first file or separated from the post. It depends on used Telegram client. This tool solves the problem by using the [bot API of Telegram](https://core.telegram.org/bots/api). I use [the method sendMediaGroup](https://core.telegram.org/bots/api#sendmediagroup) and put the post's text to the caption parameter of the last file in the media parameter.

### Link to anaglyphs

I want to attach anaglyphs to each stereo pair. But it is not comfortable to watch stereo pairs mixed with non-stereo images. It forces the watcher's eyes to defocus every image. So, I attach anaglyphs to a web page and add a link to the page to each post. Creating such pages is a routine task that interrupts my creative flow. Therefore, this tool creates the page by template and uploads it to a static hosting. This is [an example of the page](http://csscolor.ru/more/stereo/posts/2022/12/arches%20and%20outside%20pattern%20%28Astana%20Grand%20Mosque%29.html) for the post above:

![page example](./docs/page-example.png)

By the way, it is a way to back up posts and avoid keeping all my posts on only one platform. I can host the backup myself. This is not only diversification but also makes it challenging to maintain hosting my posts. I decided to host all posts as static pages and photos without any server-side engine. It is easy and chip to deploy my static files on every static storage, even on my own server.

That approach limits my pages from dynamic changes, but keeping all pages original is better.

## Installation

Install dependencies:
```commandline
pip3 install -r requirements.txt
```

It is necessary to have the following:
 - static storage with FTP access
 - Telegram bot with token
 - Telegram channel
 - the bot with admin permissions in the channel
 - chat ID of the channel (just run [getUpdates method](https://core.telegram.org/bots/api#getupdates) in a browser after adding the bot to the channel)

Fill `.env` file:
```text
FTP_SERVER = '...'
FTP_LOGIN = '...'
FTP_PASSWORD = '...'

INPUTS_BACKUP_FILEPATH = './inputs_backup.txt'

TEST_CHANNEL_ID = '...'
TELEGRAM_BOT_TOKEN = '...'

SCRIPT_ROOT_DIR = '...'
FTP_ROOT_DIR = '...'
DOMAIN_ROOT_URL = '...'
```
I recommend adding the directory with `ang` script to PATH. After that, it will be possible to use the script by typing `ang` in the command line.

## Usage and Demo

Run `ang` script and fill in inputs. 

You can use the flag `-l` or `--last` to edit the previous posting attempt.

You can also follow the instructions in [the video](https://youtu.be/QPzmLHo1Cug) below.

[![Demo: Stereo Telegram Posts Printing Press](https://img.youtube.com/vi/QPzmLHo1Cug/0.jpg)](https://www.youtube.com/watch?v=QPzmLHo1Cug "Demo: Stereo Telegram Posts Printing Press")

 