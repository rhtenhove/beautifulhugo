# Beautiful Hugo - An adaptation of the Beautiful Jekyll theme - Bootstrap v4

![Beautiful Hugo Theme Screenshot](images/screenshot.png)

## Installation
In your hugo root directory:
```bash
$ mkdir themes
$ git clone https://github.com/halogenica/beautifulhugo.git themes/beautifulhugo
``` 

## Extra Features

- Disqus
- Staticman
- [Google Analytics](https://google.com/analytics/)
- [Commit SHA in footer](commit-sha-in-the-footer)

> See `exampleSite/config.yaml` for examples and comments on how to configure these

### Responsive

This theme is designed to look great on both large-screen and small-screen (mobile) devices.

### Syntax highlighting

This theme has support for either Hugo's lightning fast Chroma or client side highlighting using `highlight.js`.

See [Hugo docs](https://gohugo.io/getting-started/configuration-markup/#highlight) on how to configure Hugo's Highlight.

### Staticman support

Add *Staticman* configuration section in `config.toml` or `config.yaml`

Sample `config.toml` configuration

```toml
[Params.staticman]
  api = "https://<API-ENDPOINT>/v3/entry/{GIT-HOST}/<USERNAME>/<REPOSITORY-BLOGNAME>/master/comments"
[Params.staticman.recaptcha]
      sitekey: "6LeGeTgUAAAAAAqVrfTwox1kJQFdWl-mLzKasV0v"
      secret: "hsGjWtWHR4HK4pT7cUsWTArJdZDxxE2pkdg/ArwCguqYQrhuubjj3RS9C5qa8xu4cx/Y9EwHwAMEeXPCZbLR9eW1K9LshissvNcYFfC/b8KKb4deH4V1+oqJEk/JcoK6jp6Rr2nZV4rjDP9M7nunC3WR5UGwMIYb8kKhur9pAic="
```

Note: The public `API-ENDPOINT` https://staticman.net is currently hitting its API limit, so one may use other API instances to provide Staticman comment service.

The section `[Params.staticman.recaptcha]` is *optional*.  To add reCAPTCHA to your site, you have to replace the default values with your own ones (to be obtained from Google.)  The site `secret` has to be encrypted with

    https://<API-ENDPOINT>/v3/encrypt/<SITE-SECRET>

You must also configure the `staticman.yml` in you blog website.

```yaml
comments:
  allowedFields: ["name", "email", "website", "comment"]
  branch            : "master"
  commitMessage     : "New comment in {options.slug}"
  path: "data/comments/{options.slug}"
  filename          : "comment-{@timestamp}"
  format            : "yaml"
  moderation        : true
  requiredFields    : ['name', 'email', 'comment']
  transforms:
    email           : md5
  generatedFields:
    date:
      type          : "date"
      options:
        format      : "iso8601"
  reCaptcha:
    enabled: true
    siteKey: "6LeGeTgUAAAAAAqVrfTwox1kJQFdWl-mLzKasV0v"
    secret: "hsGjWtWHR4HK4pT7cUsWTArJdZDxxE2pkdg/ArwCguqYQrhuubjj3RS9C5qa8xu4cx/Y9EwHwAMEeXPCZbLR9eW1K9LshissvNcYFfC/b8KKb4deH4V1+oqJEk/JcoK6jp6Rr2nZV4rjDP9M7nunC3WR5UGwMIYb8kKhur9pAic="
```

If you *don't* have the section `[Params.staticman]` in `config.toml`, you *won't* need the section `reCaptcha`  in `staticman.yml`

### Commit SHA in the footer

If the source of your site is in a Git repo, the SHA corresponding to the commit the site is built from can be shown on the footer.
To do so, two site parameters `commit` has to be defined in the config file `config.yaml`:

```yaml
enableGitInfo: true
Params:
  commit: "https://github.com/<username>/<siterepo>/tree/"
```

> See at [vincenttam/vincenttam.gitlab.io](https://gitlab.com/vincenttam/vincenttam.gitlab.io) for an example of how to add it to a continuous integration system.

### Multilingual

To allow Beautiful Hugo to go multilingual, you need to define the languages
you want to use inside the `languages` parameter on `config.toml` file, also
redefining the content dir for each one. Check the `i18n/` folder to see all
languages available.

```toml
[languages]
  [languages.en] 
    contentDir = "content/en" # English
  [languages.ja]
    contentDir = "content/ja" # Japanese
  [languages.br]
    contentDir = "content/br" # Brazilian Portuguese
```

Now you just need to create a subdir within the `content/` folder for each
language and just put stuff inside `page/` and `post/` regular directories.
```
content/      content/      content/  
└── en/       └── br/       └── ja/ 
    ├── page/     ├── page/     ├── page/
    └── post/     └── post/     └── post/

```
 
### Extra shortcodes

There are two extra shortcodes provided (along with the customized figure shortcode):

#### Details

This simply adds the html5 detail attribute, supported on all *modern* browsers. Use it like this:

```
{{% details "This is the details title (click to expand)" %}}
This is the content (hidden until clicked).
{{% /details %}}
```

#### Split

This adds a two column side-by-side environment (will turn into 1 col for narrow devices):

```
{{< columns >}}
This is column 1.
{{< column >}}
This is column 2.
{{< endcolumn >}}
```

## Self hosted
There used to be a self-hosted option, where all the imports would be part of this repo. This has been removed. I recommend using [Decentraleyes](https://decentraleyes.org/) if you'd like to keep things local.

## About

This is an adaptation of the Jekyll theme [Beautiful Jekyll](https://deanattali.com/beautiful-jekyll/) by [Dean Attali](https://deanattali.com/aboutme).
It supports most of the features of the original theme, and many new features. It has diverged from the Jekyll theme over time, with years of community updates.

## License

MIT Licensed, see [LICENSE](LICENSE).
