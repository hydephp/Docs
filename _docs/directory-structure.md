# Getting Started

To take full advantage of the framework, it may first be good to familiarize ourselves with the directory structure.

## Tree Overview
```
// torchlight! {"lineNumbers": false}
├── _docs              
├── _drafts            
├── _pages             
├── _posts             
├── _site              
├── config             
├── resources
│   └── views          
│       ├── components 
│       ├── layouts    
│       ├── pages      
├── src                
│   └── resources
│       └── sass
```

## Directory Explanation 
It may be helpful to separate the two types of directories we have.

First, we have the content directories, these are prefixed with an underscore (`_`).

Then we have the resource directories, they contain the HTML (Blade) templates and similar. If you are just getting started you may not need to dig into the second category, but they are available for you to play around with! 

Let's take a look!

### Content Directories

#### `_posts` 
This is where the blog post files are stored. Files here support YAML front matter.

You can scaffold posts using the `php hyde make:post` command with automatically creates the front matter based on your input selections.

A _posts directory filled with posts may look similar to this.
```
// torchlight! {"lineNumbers": false}
_posts
├── hello-world.md
├── my-first-post.md
├── diary-of-a-volunteer.md
├── benefits-of-milkshakes.md
└── a-fifth-longer-post-here.md
```

**Limitations:** Currently only top-level posts are supported. Files should use kebab-case format and must also end in .md and contain front matter to be recognized.

#### `_docs` 
Hyde includes a spiritual successor of [Laradocgen](https://github.com/caendesilva/laradocgen)

All you need to do to create a documentation page is to place a Markdown file in this directory and run the build command.
The sidebar will automatically be populated with the page title which is derived from the first H1 (# Title) tag.

This documentation page is built with HydeDocs, and you can take a look at the source code on https://github.com/hydephp/docs which also serves this site through GitHub Pages.

**Limitations:** Currently only top-level posts are supported. Soon (hopefully) you will be able to put files in subdirectories, or alternatively specify a parent, to create a sidebar with categories.

Files should use kebab-case format and must also end in .md and contain front matter to be recognized.

#### `_pages` 
You can also place Markdown files here and they will be compiled into simple top-level pages.

Perfect for about pages, or terms of service policy pages!

**Limitations:** Only top-level pages are supported. Files should use kebab-case format and must also end in .md and contain front matter to be recognized.

> Make sure the slug does not conflict with a custom Blade page as Markdown pages are compiled first and may be overwritten.

#### `_drafts` 
This is a good place to store posts you are not ready to post. Files in this directory are ignored by Hyde.

#### `_site` 
This is where the compiled static site is stored. You should not edit files here as they may get overwritten.

When publishing your site this is where you should serve the site from.


### Resource Directories
#### `config` 
The config directory contains configuration files. The most interesting one is probably `config/hyde.php` where you can set the site name!

#### `resources/views`
HydePHP is built on top of Laravel and utilizes Laravel's templating system called Blade. If you want to customize these templates, take a look at the dedicated section in [Customization](customization.html)

Here is a quick overview of the directories it contains though
```
// torchlight! {"lineNumbers": false}
resources
└── views // These are the Blade views, they are like HTML templates
    ├── components // These are components used in various places, extracted to be customized easy!
    ├── layouts // Main layout files
    ├── pages // This is a special directory. Pages here ending in .blade.php will be saved as .html pages in the saved site.
```

And for an explanation of each of these subdirectories:

- The `components` directory contains self-contained components used in various places, extracted to be customized easy!
- The `layouts` directory contains common components used to define the layouts, such as the app layout, head section and navigation.
- The `pages` directory is special and deserves its section which comes right away.

#### `resources/views/pages`
This is a special directory.

All files here ending in .blade.php will be saved as .html pages in the saved site.
This is useful as you can both extend the default layout, or you can write your view fully.
The latter allows for a really neat hack which is used on this site to redirect index.html to the documentation front page!

**Limitations:** Only top-level posts are supported. Files should use kebab-case format and must also end .blade.php.

> Make sure the slug does not conflict with a Markdown page as they are compiled first and will be overwritten if your Blade page has the same name.


#### `src/resources`
This directory contains source files for frontend assets such as the SASS/SCSS files.

```
// torchlight! {"lineNumbers": false}
├── src 
│   └── resources
│       └── sass
```
