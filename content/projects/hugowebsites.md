---
author: "Rob Alicea"
title: "Hugo Websites for Beginners"
date: "2023-02-05"
description: "fast, reliable, secure..."
cover:
    image: "img/9.png"
    alt: "This is an image"
ShowReadingTime: True
    
---
# Static Websites

This project was created using Fedora SilverBlue on a toolbox container, and the theme I chose is Hugo-Coder. However, you can choose any theme you like from Hugo Themes; just be sure to read the instructions of each theme before beginning and make any necessary tweaks. Use Windows, Mac OS, or another Linux distro to complete this project. Remember that certain commands will be different. Refer to the Hugo website’s quick start guide to install Hugo on your computer. Due to the grade difficulty and required processes, I feel accomplished after completing this task.

I am still learning and occasionally making mistakes on the website. The most challenging aspect of constructing a website is customizing it for my needs, which will need me to seek out further information or possibly contact the theme’s developer. For me, this is not the end; I’ve discovered that there is more and more to learn in this area. I shall take my time, but I believe it is time well spent.

### Install 

All right, let’s get started: Now, let’s check if we have Hugo in our system, install and then check the version again…
```
$ sudo dnf update
$ sudo dnf install hugo
$ hugo version
hugo v0.98.0+extended linux/amd64
```
I’m creating the required directories to maintain system order. You can skip this step and simply store the file wherever you like on your computer.
```
$ cd Documents
$ mkdir Projects && cd Projects
```
Go to GitHub and establish an account if you are a new user, or log in if you already have one. You must create two additional repositories. The first one was titled blog; scroll down and press the create button. Let’s establish another repository, but this time it must have your username. In my situation, username.github.io. This will be the web page’s address. If you have a domain, the next step is to visit netfly; however, that is outside the scope of this article.

During the process of pushing my local site to GitHub, I face a number of problems. Due to racism, a command formerly known as master was renamed to main. If you find an error, you are now aware. The system also required me to enter my GitHub username and password. For the password you’ll need to generate a token . It’s was found in a web article. To obtain your token, log in to your GitHub account, navigate to settings, scroll down, and on the right side you’ll see developer settings; click in and then follow the on-screen instructions. The beta token did not work for me. Once the token has been generated, copy it and store it in an easily accessible location, as you will need it multiple times.

This procedure did not appear in the tutorials I was following. Due to various factors, the majority of the time I’m doing something, it’s always something unique. Perhaps it’s because I’m working inside a container, because I’m missing software on my system, or because I lack experience. For anyone experiencing this problem, you are saved here.

Install Hugo and add the theme as a submodule; don’t forget to choose a theme and read the documentation. Some themes contain more information than others. I elected to make a clone of the sample site as my primary site and then customize it from there.
```
# Create site and cd into it
hugo new site my-site && cd my-site

# Clone the ReFresh theme into the themes folder
git init
git submodule add https://github.com/luizdepra/hugo-coder.git themes/hugo-coder

# Remove the default config
rm config.toml

# Copy the Example site content and configuration in my-site
cp -R themes/hugo-coder/exampleSite/* ./

# Open the site in your browser
hugo server -D
```
Locally, our website is up and running; congrats! I was receiving a different address each time I deployed this theme, as opposed to the usual localhost:1313.

### config.toml

Now that we’ve gotten the simple stuff out of the way, you can play around with your brand-new website and make any necessary adjustments to the config.toml file. This is what my one resembles:
```
baseURL = "http://www.example.com"
title = "Site tittle"
theme = "hugo-coder"
languageCode = "en"
defaultContentLanguage = "en"
paginate = 20
pygmentsStyle = "bw"
pygmentsCodeFences = true
pygmentsCodeFencesGuessSyntax = true
enableEmoji = true
# Enable Disqus comments
# disqusShortname = "yourdiscussshortname"

[params]
author = "Your Name"
# license = '<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">CC BY-SA-4.0</a>'
description = "A life journey through fitness and tech"
keywords = "blog,developer,fitness"
info = ["Full Time Fitness Trainer", "Tech Enthusiasts"]
avatarURL = "img/rob.jpg"
#gravatar = "john.doe@example.com"
dateFormat = "January 2, 2006"
since = 2012
# Git Commit in Footer, uncomment the line below to enable it
#commit = "https://github.com/luizdepra/hugo-coder/tree/"
# Right To Left, shift content direction for languagues such as Arabic
rtl = false
# Specify light/dark colorscheme
# Supported values:
# "auto" (use preference set by browser)
# "dark" (dark background, light foreground)
# "light" (light background, dark foreground) (default)
colorScheme = "auto"
# Hide the toggle button, along with the associated vertical divider
hideColorSchemeToggle = false
# Series see also post count
maxSeeAlsoItems = 5
# Custom CSS
customCSS = []
# Custom SCSS, file path is relative to Hugo's asset folder (default: {your project root}/assets)
customSCSS = []

# Custom JS
customJS = []

# Custom remote JS files
customRemoteJS = []

# If you want to use fathom(https://usefathom.com) for analytics, add this section
# [params.fathomAnalytics]
# siteID = "ABCDE"
# serverURL = "analytics.example.com" # Default value is cdn.usefathom.com, overwrite this if you are self-hosting

# If you want to use plausible(https://plausible.io) for analytics, add this section
# [params.plausibleAnalytics]
# domain = "example.com"
# serverURL = "analytics.example.com" # Default value is plausible.io, overwrite this if you are self-hosting or using a custom domain

# If you want to use goatcounter(https://goatcounter.com) for analytics, add this section
# [params.goatCounter]
# code = "code"

# If you want to use Cloudflare Web Analytics(https://cloudflare.com) for analytics, add this section
# [params.cloudflare]
# token = "token"

# If you want to use Matomo(https://matomo.org) for analytics, add this section
# [params.matomo]
# siteID = "ABCDE" # Default value is "1", overwrite this if you are cloud-hosting
# serverURL = "analytics.example.com" # For cloud-hosting, use provided URL, e.g. example.matomo.cloud

# If you want to use Google Tag Manager(https://analytics.google.com/) for analytics, add this section
# [params.googleTagManager]
# id = "gid"

# If you want to use Yandex Metrika(https://metrika.yandex.ru) for analytics, add this section
# [params.yandexMetrika]
# id = "gid"

# If you want to use Application Insights(https://azure.com/) for analytics, add this section
# [params.applicationInsights]
# connectionString = "connectionString"

# If you want to use microanalytics.io for analytics, add this section
# [params.microAnalytics]
# id = "ABCDE"
# dnt = "false" # respect DNT tracker, "true" by default

# If you want to implement a Content-Security-Policy, add this section
# [params.csp]
# childsrc = ["'self'"]
# fontsrc = ["'self'", "https://fonts.gstatic.com", "https://cdn.jsdelivr.net/"]
# formaction = ["'self'"]
# framesrc = ["'self'", "https://www.youtube.com"]
# imgsrc = ["'self'"]
# objectsrc = ["'none'"]
# stylesrc = [
#   "'self'",
#   "'unsafe-inline'",
#   "https://fonts.googleapis.com/",
#   "https://cdn.jsdelivr.net/",
# ]
# scriptsrc = [
#   "'self'",
#   "'unsafe-inline'",
#   "https://www.google-analytics.com",
#   "https://cdn.jsdelivr.net/",
# ]
# prefetchsrc = ["'self'"]
# # connect-src directive – defines valid targets for to XMLHttpRequest (AJAX), WebSockets or EventSource
# connectsrc = ["'self'", "https://www.google-analytics.com"]

[taxonomies]
category = "categories"
series = "series"
tag = "tags"
author = "authors"

[[params.social]]
name = "Github"
icon = "fa fa-2x fa-github"
weight = 1
url = "https://github.com/johndoe/"

[[params.social]]
name = "Gitlab"
icon = "fa fa-2x fa-gitlab"
weight = 2
url = "https://gitlab.com/johndoe/"

[[params.social]]
name = "Twitter"
icon = "fa fa-2x fa-twitter"
weight = 3
url = "https://twitter.com/johndoe/"

[[params.social]]
name = "LinkedIn"
icon = "fa fa-2x fa-linkedin"
weight = 4
url = "https://www.linkedin.com/in/johndoe/"

[[params.social]]
name = "Medium"
icon = "fa fa-2x fa-medium"
weight = 5
url = "https://medium.com/@johndoe"

[[params.social]]
name = "RSS"
icon = "fa fa-2x fa-rss"
weight = 6
url = "https://myhugosite.com/index.xml"
rel = "alternate"
type = "application/rss+xml"

[languages.en]
languageName = "🇬🇧"

[[languages.en.menu.main]]
name = "About"
weight = 1
url = "about/"

[[languages.en.menu.main]]
name = "Blog"
weight = 2
url = "posts/"

[[languages.en.menu.main]]
name = "Projects"
weight = 3
url = "projects/"

[[languages.en.menu.main]]
name = "Contact me"
weight = 5
url = "contact/"
```
### Conclusion:

Part 1 of this series has come to a close; it may have taken long time, but you are finally free to experiment with and modify your website as you see fit. Keep in mind that there are fascinating new discoveries to be made at every turn. In the next part, we’ll learn how to deploy a local website to GitHub Pages. Next comes the exciting part; enjoy yourself, and keep in mind that learning is a process, not a destination.