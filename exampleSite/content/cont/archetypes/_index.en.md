+++
title = "Archetypes"
weight = 10
+++

Using the command: `hugo new [relative new content path]`, you can start a content file with the date and title automatically set. While this is a welcome feature, active writers need more: [archetypes](https://gohugo.io/content/archetypes/). These are preconfigured skeleton pages with default frontmatter.

The Relearn theme defines some few archetypes of pages but you are free to define new ones to your liking. All can be used at any level of the documentation, the only difference being the layout of the content.

## Predefined Archetypes

### Home {#archetypes-home}

A **Home** page is the starting page of your project. It's best to have only one page of this kind in your project.

![Home page](images/pages-home.png?classes=shadow&width=60pc)

To create a home page, run the following command

```shell
hugo new --kind home _index.md
```

This leads to a file with the following content

```markdown
+++
archetype = "home"
title = "{{ replace .Name "-" " " | title }}"
+++

Lorem Ipsum.
```

### Chapter {#archetypes-chapter}

A **Chapter** displays a page meant to be used as introduction for a set of child pages. Commonly, it contains a simple title and a catch line to define content that can be found below it.

![Chapter page](images/pages-chapter.png?classes=shadow&width=60pc)

To create a chapter page, run the following command

```shell
hugo new --kind chapter <name>/_index.md
```

This leads to a file with the following content

```markdown
+++
archetype = "chapter"
narrow = true
title = "{{ replace .Name "-" " " | title }}"
weight = X
+++

Lorem Ipsum.
```

Replace the `X` with a number. Because this number will be used to generate the subtitle of the content page, set the number to a consecutive value starting at 1 for each new chapter level.

### Default {#archetypes-default}

A **Default** page is any other content page. If you set an unknown archetype in your frontmatter, this archetype will be used to generate the page.

![Default page](images/pages-default.png?classes=shadow&width=60pc)

To create a default page, run either one of the following commands

```shell
hugo new <chapter>/<name>/_index.md
```

or

```shell
hugo new <chapter>/<name>.md
```

This leads to a file with the following content

```markdown
+++
title = "{{ replace .Name "-" " " | title }}"
weight = X
+++

Lorem Ipsum.
```

Replace the `X` with a number or delete the whole `weight` parameter entirly.

## Selfdefined Archetypes

If you are in need of further archetypes you can define your own or even redefine existing ones.

### Template

Define a template file in your project at `archetypes/<kind>.md` and make sure it has at least the frontmatter parameter for that archetype like

````markdown
+++
archetype = "<kind>"
+++
````

Afterwards you can generate new content files of that kind with the follwing command

```shell
hugo new --kind <kind> <name>/_index.md
```

### Partial

To define how your archetypes are rendered, define a corresponding file in your project at `layouts/partials/archetypes/<kind>.html`.

Take a look at the existing archetypes of this theme to get an idea how to utilize it.

If you use an unknown archetype in your frontmatter, the `default` archetype will be used to generate the page.