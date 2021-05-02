---
weight: 4
title: "Shortcodes"
subtitle: ""
date: 2021-01-10T15:37:14+08:00
lastmod: 2021-01-10T15:37:14+08:00
draft: false
author: "Wen-Wei Tseng"
authorLink: "https://sosiristseng.github.io/"
description: "This article shows the Hugo shortcodes."

tags: ["shortcodes"]
categories: ["Hugo"]

hiddenFromHomePage: false
hiddenFromSearch: false

featuredImage: "featured-image.jpg"
featuredImagePreview: "featured-image-preview.jpg"

toc:
  enable: true
math:
  enable: false
lightgallery: true
---

A list of shortcodes supported by my template site.

<!--more-->

## Hugo shortcodes

Hugo's [built-in shoorcodes](https://gohugo.io/content-management/shortcodes).

### figure {#figure}

```markdown
{{</* figure src="/images/lighthouse.jpg" title="Lighthouse (figure)" */>}}
```

The rendered output looks like this:

{{< figure src="/images/lighthouse.jpg" title="Lighthouse (figure)" >}}

### gist

```
{{</* gist spf13 7896402 */>}}
```

The rendered output looks like this:

{{< gist spf13 7896402 >}}

### highlight

```
{{</* highlight go "linenos=table,hl_lines=8 15-17,linenostart=199" */>}}
// Code content
{{</* /highlight */>}}
```

{{< highlight go "linenos=table,hl_lines=8 15-17,linenostart=199" >}}
// GetTitleFunc returns a func that can be used to transform a string to
// title case.
//
// The supported styles are
//
// - "Go" (strings.Title)
// - "AP" (see https://www.apstylebook.com/)
// - "Chicago" (see https://www.chicagomanualofstyle.org/home.html)
//
// If an unknown or empty style is provided, AP style is what you get.
func GetTitleFunc(style string) func(s string) string {
  switch strings.ToLower(style) {
  case "go":
    return strings.Title
  case "chicago":
    tc := transform.NewTitleConverter(transform.ChicagoStyle)
    return tc.Title
  default:
    tc := transform.NewTitleConverter(transform.APStyle)
    return tc.Title
  }
}
{{< /highlight >}}

### param

```markdown
{{</* param description */>}}
```

{{< param description >}}

### ref and relref {#ref-and-relref}

```markdown
See the [about page]({{</* ref "about" */>}}) for example.
```

See the [about page]({{< ref "about" >}}) for example.

### tweet

```markdown
{{</* tweet 1344690082792542211 */>}}
```

{{< tweet 1344690082792542211 >}}

### vimeo

```markdown
{{</* vimeo 146022717 */>}}
```

{{< vimeo 146022717 >}}

### youtube

```markdown
{{</* youtube w7Ft2ymGmfc */>}}
```

{{< youtube w7Ft2ymGmfc >}}

## Added by CodeIT theme

I only listed the shortcodes I use the most. See the [original extended shortcode documentation](https://codeit.suntprogramator.dev/theme-documentation-extended-shortcodes/) for the full list.

### image {#image}

`image` shortcode is an alternative to [`figure` shortcode](../theme-documentation-built-in-shortcodes#figure). `image` shortcode can take full advantage of the dependent libraries of [lazysizes](https://github.com/aFarkas/lazysizes) and [lightgallery.js](https://github.com/sachinchoolur/lightgallery.js).

The complete usage of [local resource references](../theme-documentation-content#contents-organization) is supported.

The `image` shortcode has the following named parameters:

- **src** _[required]_ (**first** positional parameter)

  URL of the image to be displayed.

- **alt** _[optional]_ (**second** positional parameter)

  Alternate text for the image if the image cannot be displayed, default value is the value of **src** parameter.

  _Markdown or HTML format is supported._

- **caption** _[optional]_ (**third** positional parameter)

  Image caption.

  _Markdown or HTML format is supported._

- **title** _[optional]_

  Image title that will be shown when hovering on the image.

- **class** _[optional]_

  `class` attribute of the HTML `figure` tag.

- **src_s** _[optional]_

  URL of the image thumbnail, used for lightgallery, default value is the value of **src** parameter.

- **src_l** _[optional]_

  URL of the HD image, used for lightgallery, default value is the value of **src** parameter.

- **height** _[optional]_

  `height` attribute of the image.

- **width** _[optional]_

  `width` attribute of the image.

- **linked** _[optional]_

  Whether the image needs to be hyperlinked, default value is `true`.

- **rel** _[optional]_

  Additional `rel` attributes of the HTML `a` tag, if **linked** parameter is set to `true`.

Example `image` input:

```markdown
{{</* image src="/images/lighthouse.jpg" caption="Lighthouse (`image`)" src_s="/images/lighthouse-small.jpg" src_l="/images/lighthouse-large.jpg" */>}}
```

The rendered output looks like this:

{{< image src="/images/lighthouse.jpg" caption="Lighthouse (`image`)" src_s="/images/lighthouse-small.jpg" src_l="/images/lighthouse-large.jpg" >}}

### admonition

The `admonition` shortcode supports **12** types of banners to help you put notice in your page.

_Markdown or HTML format in the content is supported._

{{< admonition >}}
A **note** banner
{{< /admonition >}}

{{< admonition abstract >}}
An **abstract** banner
{{< /admonition >}}

{{< admonition info >}}
A **info** banner
{{< /admonition >}}

{{< admonition tip >}}
A **tip** banner
{{< /admonition >}}

{{< admonition success >}}
A **success** banner
{{< /admonition >}}

{{< admonition question >}}
A **question** banner
{{< /admonition >}}

{{< admonition warning >}}
A **warning** banner
{{< /admonition >}}

{{< admonition failure >}}
A **failure** banner
{{< /admonition >}}

{{< admonition danger >}}
A **danger** banner
{{< /admonition >}}

{{< admonition bug >}}
A **bug** banner
{{< /admonition >}}

{{< admonition example >}}
An **example** banner
{{< /admonition >}}

{{< admonition quote >}}
A **quote** banner
{{< /admonition >}}

The `admonition` shortcode has the following named parameters:

- **type** _[optional]_ (**first** positional parameter)

  Type of the `admonition` banner, default value is `note`.

- **title** _[optional]_ (**second** positional parameter)

  Title of the `admonition` banner, default value is the value of **type** parameter.

- **open** _[optional]_ (**third** positional parameter)

  Whether the content will be expandable by default, default value is `true`.

Example `admonition` input:

```markdown
{{</* admonition type=tip title="This is a tip" open=false */>}}
A **tip** banner
{{</* /admonition */>}}
Or
{{</* admonition tip "This is a tip" false */>}}
A **tip** banner
{{</* /admonition */>}}
```

The rendered output looks like this:

{{< admonition tip "This is a tip" false >}}
A **tip** banner
{{< /admonition >}}

## Ported from `color your world`

Some useful shortcodes were ported from the [color your world](https://gitlab.com/rmaguiar/hugo-theme-color-your-world) theme.

### abbr

The HTML `<abbr>` tag.

```
{{</* abbr "idk" "I don't know" */>}}
```

The rendered output looks like this:

{{< abbr "idk" "I don't know" >}}

### kbd

The HTML `<kbd>` tag.

```
{{</* kbd "Ctrl" "Shift" "i" */>}}
```

The rendered output looks like this:

{{< kbd "Ctrl" "Shift" "i" >}}

### gifoid

The `gifoid` shortcode plays `filename.mp4` or `filename.webm` in a loop to look like {{< abbr "GIF" "Graphics Interchange Format" >}}.

```
{{</* gifoid filename */>}}
```

The rendered output looks like this:

{{< gifoid "birb" "Cute boi" >}}


By default it searches videos files in the `video` subfolder, but you can change that by setting `videoPath: "<path>"` in the frontmatter.
