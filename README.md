# cf-cloudflare-worker-s3-uploader

# 🚀 Cloudflare Worker for uploading images to Amazon S3 🚀

https://github.com/coding-to-music/cf-cloudflare-worker-s3-uploader

From / By https://github.com/yusukebe/cf-s3-uploader

## Environment variables:

wrangler.example.toml

```java
account_id = ""
compatibility_date = "2021-11-01"
name = "s3-uploader"
route = ""
type = "javascript"
workers_dev = true
zone_id = ""

[site]
bucket = "./public"
entry-point = "./"

[build]
command = "npm install && npm run build"
[build.upload]
format = "service-worker"

[vars]
S3_BUCKET = "your_bucket_name"
S3_FOLDER = "folder-name/"
S3_REGION = "s3_region_name"

[secrets]
# NAME
# PASS
# AWS_ID
# AWS_SECRET
```

## GitHub

```java
git init
git add .
git remote remove origin
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:coding-to-music/cf-cloudflare-worker-s3-uploader.git
git push -u origin main
```

# cf-s3-uploader

Cloudflare Worker for uploading images to Amazon S3.

## Set up

First, git clone:

```bash
$ https://github.com/yusukebe/cf-s3-uploader.git
$ cd cf-s3-uploader
```

Copy `wrangler.exmple.toml` to `wrangler.tmol`:

```bash
$ cp wrangler.example.toml wrangler.toml
```

## Variables

### Environment variables

Enviroment variables are:

- `S3_BUCKET` - Your S3 bucket name
- `S3_REGION` - S3 region name

To set these, `wrangler.toml`

```toml
[vars]
S3_BUCKET = "your_bucket_name"
S3_REGION = "s3_region_name"
```

### Secret variables

Secret variables are:

- `NAME` - User name of basic auth
- `PASS` - User password of basic auth
- `AWS_ID` - AWS access key ID
- `AWS_SECRET` - AWS secret access key

To set these, use `wrangler secret put` command:

```bash
$ wrangler secret put NAME
```

## Publish

To publish to your Cloudflare Workers:

```bash
$ wrangler publish
```

## Endpoints

### `/upload`

Header:

To pass the Basic Auth, add the Base64 string of "user:pass" to `Authorization` header.

```
Authorization: Basic ...
```

Body:

Value of `body` is Basic64 string of image binary.

```json
{
  "body": "Base64 Text..."
}
```

## Use with Shortcuts

Awesome!!!

![Screenshot](https://user-images.githubusercontent.com/10682/139781916-8c22a6ae-b21b-48ff-ad1c-08d396f5cdd0.gif)

Setting shortcuts like this:

![Screenshot](https://s3.ap-northeast-1.amazonaws.com/yusukebe.com/images/57f68c29ea5d0af4e9480ad04e89d152.png)

## Author

Yusuke Wada <https://github.com/yusukebe>

## LICENSE

MIT
