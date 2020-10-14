# RdvSpeakers Theme Hugo

RdvSpeakers Theme Hugo is a theme for conferences/events.

It's based on the GDG Toulouse's DevFest Theme Hugo.

See a real usage here: <https://rdv-speakers.fr/>

## Building my conference site from scratch

1. Install [Hugo](https://gohugo.io)
2. Create a new site by running:

```bash
hugo new site my-conf
cd my-conf
mkdir themes
git submodule add https://github.com/RdvSpeakers/rdvspeakers-theme-hugo.git themes/rdvspeakers-theme-hugo
```

3. Then edit your `config.toml` file with

```toml
# ...
theme = "rdvspeakers-theme-hugo"
# ...
```


4. It's done. Just start Hugo server to see it live!

```bash
hugo server
```

## Customizing the site

`yarn` to install the dependency

Run `npm start` to watch Sass changes.

When you are happy with the result run `npm run build` to build the minified version

### Site params


```toml
#...


enableEmoji = true
enableRobotsTXT = true
enableMissingTranslationPlaceholders = true

googleAnalytics = "UA-XXXXXXXX-X"

[params]
    title = "Le Halloween des Speakers 2020"
    date = "2020-02-28"
    description = "*Le Halloween des Speakers* is a technical conference for developers, organized by *Les Rendez-vous des Speakers* association. Taking into account the health situation, the 2020 edition of *Le Halloween des Speakers* will be online..."
    images = ["/images/social-share.jpg"]
    email = "rentreespeakers@gmail.com"
    keywords = "event, conference, speakers, programming, developers"
    copyright = "We ❤️️ speakers"
    subscriptionUrl = ""
    sponsorshipUrl=""
    appleTouchIcon = "/apple-touch-icon.png"
    favicon48 = "/favicon-48x48.png"
    favicon32 = "/favicon-32x32.png"
    favicon16 = "/favicon-16x16.png"
    manifest = "/manifest.json"
    safariPinnedTab = "/safari-pinned-tab.svg"
    themeColor = "#4d4d4d"
    env="production"

[params.logos]
    jumbo = "/images/logos/logo_color_text.png"
    header = "/images/logos/logo_color_text.png"
    footer = "/images/logos/logo_gray_text.png"


[languages]
[languages.en]
    weight = 1
    languageName = "gb"

[languages.fr]
    weight = 2
    languageName = "fr"

[languages.fr.params]
    description = "*Le Halloween des Speakers*, est une conférence technique organisée par l'association *Les Rendez-vous des Speakers* et destinée aux développeurs et développeuses. Elle s'adresse aussi bien aux étudiant•e•s, aux professionnels ou tout simplement aux curieux et curieuses technophiles. Situation sanitaire oblige, l'édition 2020 de *Le Halloween des Speakers* se fera en ligne."

[taxonomies]
  tag = "tags"
#...
```

### Header

The top navigation bar is build with

* Site title
* Site parameter `logos.header` for the logo
* Site languages if you need a multilingual site
* Menu `main`

### Footer

The footer is build with

* Site title
* Site params `email`, `subscriptionUrl`, `logos.footer`, `copyright`
* data from `data/footer.yml`


```yml
share:
  - name: facebook
    url: https://rentreespeakers.fr/
  - name: twitter
    url: https://rentreespeakers.fr/

follow:
  - name: twitter
    url: https://twitter.com/RentreeSpeakers

content:
  - title: footer_about
    links:
      - nameKey: footer_coc
        url: /code-of-conduct/
        newTab: false
```

### Home

The Home page is build with markdown and calling some shortcodes. 

#### Jumbo bloc

```hugo

{{% jumbo img="/images/backgrounds/back-01.jpg" imgLabel="La Rentrée des Speakers 2020" %}}


## October 26th-30th, 2020
### Online

{{% /jumbo %}}

```

#### Info block

With main description and key figures.

```hugo
{{% home-info what="Attendees:150,Days:5,Sessions:12" class="primary" %}}

## What is *Le Halloween des Speakers*?

*Le Halloween des Speakers* is a technical conference for developers, organized by *Les Rendez-vous des Speakers* association. 


Taking into account the health situation, the 2020 edition of *Le Halloween des Speakers* will be online...
{{% /home-info %}}
```

![](images/block-info.png)


#### Feature speakers block

Just present your feature speakers

```hugo
{{% home-speakers %}}
## Featured Speakers

{{< button-link label="Submit a presentation"
                url="http://www.conference-hall.io"
                icon="cfp" >}}

{{< button-link label="See all speakers"
                url="./speakers"
                icon="right" >}}

{{% /home-speakers %}}
```

![](images/feature-speakers.png)


#### Subscription block

Call to subscribe

Use the site param `subscriptionUrl`.

```hugo
{{% home-subscribe  class="primary" %}}

## Get notified about the important conference updates

{{% /home-subscribe %}}
```

![](images/subscribe.png)


### Ticket block

Display ticket information.

```hugo
{{% home-tickets %}}
# Tickets

<ul>  
<li>{{< ticket name="Blind Birds"
           starts="2019-04-04"
           ends="2019-11-08"
           price="40 €"
           info="50 first places"
           soldOut="true"
           url="https://www.billetweb.fr/devfest-toulouse-2019" >}}</li>
<li>{{< ticket name="Early Birds"
           starts="2019-04-04"
           ends="2019-11-08"
           price="60 €"
           info="70 first places"
           soldOut="true"
           url="https://www.billetweb.fr/devfest-toulouse-2019" >}}</li>
<li>{{< ticket name="Normal"
           starts="2019-04-04"
           ends="2019-11-08"
           price="80 €"
           info="250 last places"
           soldOut=""
           url="https://www.billetweb.fr/devfest-toulouse-2019" >}}</li>
</ul>

\* Your ticket gives you access to all conferences, coffee breaks, and lunch. Accommodation is NOT included in this price.

{{% /home-tickets %}}
```

![](images/block-ticket.png)

#### Location block

Show conference location.

```hugo
{{% home-location
    image="/images/map.jpg"
    address="11 Espl. Compans Caffarelli, 31000 Toulouse"
    latitude="43.6110956"
    longitude="1.4332799" %}}

## The venue

### Centre de Congrès Pierre Baudis

The Centre de Congrès Pierre Baudis is a modern place of exchange,
located on a privileged location,
in the immediate vicinity of the centre of Toulouse and in a green environment.

{{% /home-location %}}
```

![](images/block-map.png)

### Partners block

Show your partners

```hugo
{{% partners categories="platinium,gold,soutien,media,communautes" %}}
# Partners
{{% /partners %}}
```

![](images/block-partners.png)

#### Album block

```hugo
{{% album images="/images/album/2018/_25A9313.jpg,/images/album/2018/_25A9386.jpg,/images/album/2018/_25A9671.jpg,/images/album/2018/_25A9334.jpg,/images/album/2018/_25A9282.jpg,/images/album/2018/_25A9612.jpg,/images/album/2018/_25A9452.jpg,/images/album/2018/_25A9628.jpg" %}}

### Some pictures of the **DevFest Toulouse 2018** with the 👾 _retro-gaming_ theme.

<a class="btn primary" target="_blank" rel="noopener" href="https://photos.app.goo.gl/nJYFVReFUk9mnXbv9">
    See all photos
    {{% icon "right" %}}
</a>

{{% /album  %}}
```

![](images/block-album.png)


### Partners

A partner should have this params : 

```yaml
title: NAME
type: partner
category: soutien
website: 'https://example.com/'
logo: /images/partners/partner.jpg
socials: []
```

### Speakers

A speaker should have this params :

```yaml
id: jane_doe
name: Mme Jane Doe 
company: Super Company
featured: false
photo: /images/speakers/jane_doe.jpg
socials:
  - icon: twitter
    link: 'https://twitter.com/jane_doe'
    name: '@jane_doe'
  - icon: github
    link: 'https://github.com/jane_doe'
    name: jane_doe
shortBio: "Short bio"
companyLogo: /images/speakers/company/company.jpg
country: 'City, Country'
```

The body of the file is used as long bio.

### Sessions

<!> this is not yet stable

A sessions should have this params :

```yaml
id: an_id
title: Super mega title
language: Français
complexity: Beginner
tags:
  - Category
presentation: URL of slides
videoId: Youtub video id
speakers:
  - speaker id
talkType: Keynote
```

The body of the file is used as description.

### Team

A team member should have these params:

```yaml
title: Name
type: core
subtitle: ''
photo: photo.jpg
socials:
  - link: 'https://twitter.com/XXX'
    name: Twitter
  - link: 'https://www.linkedin.com/XXX'
    name: LinkedIn
```

### Blog

A blog should have these params:

```yaml
title: Title
brief: Short brief
image: /images/blog/photo.jpeg
date: 2019-01-20
draft: false
```

And of course, the body is the blog post.

### TODO Schedule

Development scheduled to summer 2019.

### FAQ, Code of Conduct, ...

just classique markdown file, this the `menu.main.weight: 80` to be displayed into the navbar.


### Notes

* We focus on English and French in this theme, so with other language, you should add months into the `layouts/partials/date-short.html`

## License

MIT, see [LICENSE](https://github.com/jweslley/hugo-conference/blob/master/LICENSE).
