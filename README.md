# Cloudflare® CLI

Command line tools for [Cloudflare](https://cloudflare.com)

## Installation

To install, place `cloudflare-cli` anywhere in your PATH. Optionally alias it to something easier, like `cfcli`.
Or just run the following command to install it as `cfcli`.

```bash
sudo wget -qO cfcli https://git.io/cfcli && sudo chmod +x ./cfcli && sudo install ./cfcli /usr/local/bin/cfcli
```

## Configuration

### Cloudfile

The easiest way to run this per project is to keep a Cloudfile in your project's root directory.

There are three variables needed to purge any cache:

* Your API key (get it [here](https://www.cloudflare.com/a/account/my-account))
* Your email (for your Cloudflare account)
* The site's "zone". If you don't know this, you can set a site instead, and `cloudflare-cli` will look up the zone

So, your cloudfile would look like this:

```bash
CLOUDFLARE_API_KEY=myCloudflareAPIKey
CLOUDFLARE_EMAIL=me@email.com
CLOUDFLARE_SITE=mysite.com
```

Or perhaps:

```bash
CLOUDFLARE_API_KEY=myCloudflareAPIKey
CLOUDFLARE_EMAIL=me@email.com
CLOUDFLARE_ZONE=123eqw7iqtas
```

### Environment Variables

You may have noticed that the Cloudfile looks a lot like bash variable assignments. That's because it is!

So you can also set each of those values by environment variable.

### Site Name

You can save the effort of setting your site name in the Cloudfile by instead placing a file called `CNAME` in the root of your project, containing only the site name.

This is particularly useful for sites hosted on Github pages, which depend on a `CNAME` file for custom domain names.

### You can also pass in some or all as flags with your command:

```bash
  -z     The Cloudflare zone
  -s     Site name, eg mysite.com
         This is not required if a zone is defined
  -e     The email address associated with your Cloudflare account
  -k     Your Cloudflare API key
```

## Commands

### Zone

`cloudflare-cli zone`

This will display the zone corresponding to your site. This may be helpful if you'd prefer to set the zone in your config, rather than looking it up each time. (This will make things a bit snappier.)

### Purge

`cloudflare-cli purge`

This will purge all of the files cached by Cloudflare for your site. It's very fast to run.

## Contributing

Fork the repo, and submit a pull request!

## More

Read more on [my website](https://petercompernolle.com/2016/purging-cloudflare-cache).
