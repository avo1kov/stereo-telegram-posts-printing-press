# Stereo Telegram Posts Printing Press

## What is it

It is a tool for creation specific posts for my Telegram [channel](https://t.me/stereobyavolkov) with stereo photos.

## Solved problems
I post stereo pairs as messages with grouped jpeg files and captions for the last file. [Example of the post](https://t.me/stereobyavolkov/83) looks like this:

<img src="./docs/post-example.png" width="350" alt="post example" />

This post have some features:
1. Description under list of files
2. Link to anaglyphs

Let's consider each feature.

### Description under list of files

It is matter to post few files in the one post to avoid user annoying due to notifications flood. And this is the problem to post it manually. Description can be attached to the first file or be separated from the post. It depends on used Telegram client. This tool solves the problem by using the [bot API of Telegram](https://core.telegram.org/bots/api). I use [method sendMediaGroup](https://core.telegram.org/bots/api#sendmediagroup) and put text of post to `caption` of the last file in `media` parameter.

### Link to anaglyphs

I want to attach anaglyphs to each stereo pair. But it is not comfortable watch stereo pairs mixed with non-stereo photos. It forces watcher's eyes to defocus every image. So, I attach anaglyphs to page and add link to page to each post. Creation of pages like that is a routine task that interrupt my creative flow. Therefore, this tool creates page by template and uploads it to static hosting. This is [example of page](http://csscolor.ru/more/stereo/posts/2022/12/arches%20and%20outside%20pattern%20%28Astana%20Grand%20Mosque%29.html) for the post above:

![page example](./docs/page-example.png)

By the way, it is way to backup posts and avoid keeping all my posts on only one platform. I can host backup myself. This is not only diversification, but this is also difficulty to maintain hosting my posts. So, I decided to host all posts like static pages and photos without any server-side engine. It is easy and chip to deploy my static files on every static storage, even on my own server.

That approach limits my pages from dynamic changes, but I find it good to keep all pages in origin form.

## Installation

Install dependencies:
```commandline
pip3 install -r requirements.txt
```

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

I recommend to add directory with `ang` script to PATH. After that it will be possible to use script just by typing `ang` in the command line.

## Usage and Demo

Run `ang` script and fill inputs.
You can use flag `-l` or `--last` to edit the last posting attempt.

You can also follow instructions in [the video](https://youtu.be/QPzmLHo1Cug) below.

[![Demo: Stereo Telegram Posts Printing Press](https://img.youtube.com/vi/QPzmLHo1Cug/0.jpg)](https://www.youtube.com/watch?v=QPzmLHo1Cug "Demo: Stereo Telegram Posts Printing Press")

 