# Elegant and Powerful Static App Builder

<p> 
    <a href="https://packagist.org/packages/hyde/hyde"><img style="display: inline; margin: 4px 2px;" src="https://img.shields.io/packagist/v/hyde/hyde" alt="Latest Version on Packagist" title="Latest version of Hyde/Hyde"></a>
    <a href="https://packagist.org/packages/hyde/framework"><img style="display: inline; margin: 4px 2px;" src="https://img.shields.io/packagist/v/hyde/framework?include_prereleases" alt="Latest Version on Packagist" title="Latest version of Hyde/Framework"></a> 
    <a href="https://packagist.org/packages/hyde/framework"><img style="display: inline; margin: 4px 2px;" src="https://img.shields.io/packagist/dt/hyde/framework" alt="Total Downloads on Packagist"></a> 
    <a href="https://github.com/hydephp/hyde/blob/master/LICENSE.md"> <img style="display: inline; margin: 4px 2px;" src="https://img.shields.io/github/license/hydephp/hyde" alt="License MIT"> </a>
    <a href="https://hydephp.github.io/developer-tools/coverage-report/"><img style="display: inline; margin: 4px 2px;" src="https://cdn.desilva.se/microservices/coverbadges/badges/9b8f6a9a7a48a2df54e6751790bad8bd910015301e379f334d6ec74c4c3806d1.svg" alt="Test Coverage" title="Average coverage between categories"></a>
    <img style="display: inline; margin: 4px 2px;" src="https://github.com/hydephp/framework/actions/workflows/test-suite.yml/badge.svg" alt="Test Suite">  <img style="display: inline; margin: 4px 2px;" src="https://github.styleci.io/repos/472503421/shield?branch=master" alt="StyleCI Status"> </a>
</p>

## ⚠ Beta Software Warning
Heads up! HydePHP is still new and currently in beta. Please report any bugs and issues in the appropriate issue tracker. Versions in the 0.x series might not be stable and may change at any time. No backwards compatibility guarantees are made and there will be breaking changes without notice.

Please wait until v1.0 for production use and remember to back up your source files before updating (use Git!). See https://hydephp.github.io/docs/master/updating-hyde.html for the upgrade guide.
## About HydePHP

HydePHP is a new Static Site Builder focused on writing content, not markup. With Hyde, it is easy to create static websites, blogs, and documentation pages using Markdown and (optionally) Blade.

Hyde is powered by Laravel Zero which is a stripped-down version of the robust Laravel Framework. Using Blade templates the site is intelligently compiled into static HTML.

Hyde is inspired by JekyllRB and is created for Developers who are comfortable writing posts in Markdown. It requires virtually no configuration out of the box as it favours convention over configuration.
This is what makes Hyde different from other Laravel static site builders that are more focused on writing your blade views from scratch, which you can do with Hyde too if you want.

Hyde is designed to be stupidly simple to get started with, while also remaining easily hackable and extendable. Hyde comes with a lightweight minimalist frontend layout built with TailwindCSS which you can extend and customize with the Blade components.

Due to this powerful modularity yet elegant simplicity, Hyde is a great choice for developers no matter what their background or experience level. Here are some ideas for what you can do with Hyde:

- You are a Laravel developer and want to build a static site without having to learn a new framework. Why not use Hyde, and take advantage of the built-in Blade support?
- You just want to write blog posts in Markdown and not have to worry about anything else. Give Hyde a try and see if it helps you out.
- You want to get a documentation site up and running quickly, allowing you to focus on content.


## Installation Quick Start
> Full installation guide is at  https://hydephp.github.io/docs/master/installation.html

The recommended method of installation is using Composer.

```bash
composer create-project hyde/hyde --stability=dev
```

For the best experience you should have PHP >= 8.0, Composer, and NPM installed.

## Getting Started
See the [Getting Started Documentation](https://hydephp.github.io/docs/master/getting-started.html) page for the full guide, and examples.

### Creating blog posts
Blog posts are Markdown files that are stored in the `_posts` directory.

They support YAML Front Matter for metadata. You can scaffold post files using the `php hyde make:post` command to automatically generate the front matter.

### Creating documentation pages
With Hyde, writing documentation is fun again! To create a documenation page, literally all you need to do is place a Markdown file in the `_docs` directory. You don't need to worry as front matter, as Hyde automatically generates the page title based on the first heading, or the filename if no heading is found.

### Creating static pages
#### Markdown pages
You can create Markdown based pages by putting Markdown files in the `_pages` directory. They will then be compiled into a simple HTML page. Front matter is optional, as the page title can be generated in the same way as documentation pages.
#### Blade pages
If you want more control over your pages, you can create Blade pages by putting views in the `_pages` directory. You can of course use Blade components within your views, they are stored in the resources/views/compomnents directory same as in Laravel.

#### A note on filenames
Hyde uses the `.md` extension for Markdown files and the `.blade.php` extension for Blade files. When compiling, the files will keep their base filenames, but with the extension renamed to `.html`. For example, the file `_posts/my-post.md` will be compiled to `_site/posts/my-post.html`.


#### Building the static site
When you have all your content ready, you can build the static site by running the `php hyde build` command.

Your site will then be saved in the `_site` directory, which you can then upload to your static web host.

If your site is missing the stylesheets you may need to run `npm install && npm run dev` to build the them.

### How it works
Hyde scans the source directories prefixed with _underscores for Markdown files and intelligently compiles them into static HTML using Blade templates automatically assigned depending on the source file. The site is then saved in _site.

Hyde is "blog and documentation aware" and has built-in templates for both blogging and for creating beautiful documentation pages based on Laradocgen. Since Hyde is modular you can of course disable the modules you don't need.

All links use relative paths, so you can deploy to a subdirectory without any problems which also makes the site work great when browsing the HTML files locally even without a web server.

### Serve a live preview
Use `php hyde serve` to start the realtime compiler and access your site from [localhost:8080](http://localhost:8080/).

### NPM Commands
See all commands in the documentation [Console Commands](https://hydephp.github.io/docs/master/console-commands.html)
Hyde optionally uses NPM to compile TailwindCSS using Laravel Mix. Run it with `npm run dev/prod/watch`.

## Hacking Hyde
Hyde is designed to be easy to use and easy to customize and hack. You can modify the source views and SCSS, customize the Tailwind config, and you can even create 100% custom HTML and Blade pages that get compiled into static HTML.

While Hyde favours "convention over configuration" there are serveral config options in the `config/hyde.php` file. All settings are prefilled with sensible defaults so you don't need to configure anything unless you want to!

## Extensions
Hyde comes with built-in support for Torchlight Syntax Highlighting.
All you need to do is to set your API token in your .env file and
Hyde will automatically enable the CommonMark extension.

> Note that when using Torchlight the pages will take longer to generate as API calls need to be made.
> However, Torchlight caches the response so this mostly affects the first time running the build, or if you update the page.

## Known Issues
Currently, only top-level custom pages are supported. In the future, nested pages will be supported.
For example, _site/directory/page.html