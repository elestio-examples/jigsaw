# Jigsaw Blog Starter Template demo CI/CD pipeline

<a href="https://dash.elest.io/deploy?source=cicd&social=Github&url=https://github.com/elestio-examples/jigsaw"><img src="source\assets\images\deploy-on-elestio.png" alt="Deploy on Elest.io" width="180px" /></a>


This is a starter template for creating a beautiful, customizable blog in Jigsaw with minimal effort. You’ll only have to change a few settings and you’re ready to go.

[View a preview of the blog template.](http://jigsaw-blog-template.tighten.co/)

## Installation

After installing Jigsaw, run the following command from your project directory:

```bash
./vendor/bin/jigsaw init blog
```

This starter template includes samples of common page types, and comes pre-configured with:

- A fully responsive navigation bar
- [Tailwind CSS](https://tailwindcss.com/), a utility CSS framework that allows you to customize your design without touching a line of CSS
- [Purgecss](https://www.purgecss.com/) to remove unused selectors from your CSS, resulting in smaller CSS files
- Syntax highlighting using [highlight.js](https://highlightjs.org/)
- A script that automatically generates a `sitemap.xml` file
- A custom 404 page
- A component for accepting signups for a [Mailchimp](https://mailchimp.com/) newsletter
- A sample contact form
- A search bar powered by [Fuse.js](http://fusejs.io/) and [Vue.js](https://vuejs.org/), which indexes your content automatically and requires zero configuration

---

![Blog starter template screenshot](https://user-images.githubusercontent.com/357312/50345466-355c7700-04fd-11e9-83dd-f4e13ecdc97c.png)

---

### Configuring your new site

As with all Jigsaw sites, configuration settings can be found in `config.php`; you can update the variables in that file with settings specific to your site. You can also add new configuration variables there to use across your site; take a look at the [Jigsaw documentation](http://jigsaw.tighten.co/docs/site-variables/) to learn more.

```php
// config.php
return [
    'baseUrl' => 'https://my-awesome-jigsaw-site.com/',
    'production' => false,
    'siteName' => 'My Site',
    'siteDescription' => 'Give your blog a boost with Jigsaw.',
    ...
];
```

> Tip: This configuration file is also where you’ll define any "collections" (for example, a collection of the contributors to your site, or a collection of blog posts organized by topic). Check out the official [Jigsaw documentation](https://jigsaw.tighten.co/docs/collections/) to learn more.

---

### Adding Content

You can write your content using a [variety of file types](http://jigsaw.tighten.co/docs/content-other-file-types/). By default, this starter template expects your content to be located in the `source/_posts/` folder.

The top of each content page contains a YAML header that specifies how it should be rendered. The `title` attribute is used to dynamically generate HTML `title` and OpenGraph tags for each page. The `extends` attribute defines which parent Blade layout this content file will render with (e.g. `_layouts.post` will render with `source/_layouts/post.blade.php`), and the `section` attribute defines the Blade "section" that expects this content to be placed into it.

```yaml
---
extends: _layouts.post
section: content
title: Getting Started
date: 2018-12-25
description: Getting started with the Jigsaw blog starter template
cover_image: /assets/img/post-cover-image-2.png
featured: true
---
```

---

### Adding Assets

Any assets that need to be compiled (such as JavaScript, Less, or Sass files) can be added to the `source/_assets/` directory, and Laravel Mix will process them when running `npm run dev` or `npm run prod`. The processed assets will be stored in `/source/assets/build/` (note there is no underscore on this second `assets` directory).

Then, when Jigsaw builds your site, the entire `/source/assets/` directory containing your built files (and any other directories containing static assets, such as images or fonts, that you choose to store there) will be copied to the destination build folders (`build_local`, on your local machine).

Files that don't require processing (such as images and fonts) can be added directly to `/source/assets/`.

[Read more about compiling assets in Jigsaw using Laravel Mix.](http://jigsaw.tighten.co/docs/compiling-assets/)

---

## Building Your Site

Now that you’ve edited your configuration variables and know how to customize your styles and content, let’s build the site.

```bash
# build static files with Jigsaw
./vendor/bin/jigsaw build

# compile assets with Laravel Mix
# options: dev, prod
npm run dev
```

<img src="source\assets\images\screenshot.png" alt="screenshot of the example app" width="100%" />


## CI/CD on Elestio

Showing here how to deploy to Elestio.

# Steps to create CI/CD pipeline on elestio

### Step 1: Select CI/CD from left sidebar in app.

Click [here](https://dash.elest.io/deploy?source=cicd) to directly go to the CI/CD

### Step 2: Select Deployment method.

We have three different types of deployment method

- Github
- Gitlab
- Docker compose

But for this Jigsaw Template, you can choose GitHub as your deployment method.

### Step 3: Authentication

Select Clone in step at step Git Repository and select Jigsaw template for creating a repository in your git account after that authenticate with Git by clicking on
Continue with Github button and authorize elestio to access git then you can rename you repository name if you want.

Else If you forked the repo then you can click on the Continue with GitHub button and authorize elestio to access the git repo then you can select the jigsaw repo otherwise you can directly insert a git repo URL to deploy the Jigsaw Template.

### Step 4: Configuration

After selecting a repo or inserting a URL it will auto-filled all the desired configurations using the elestio.yml/elestio.json file.

You can also manually customize the Configure your application. 

Select your runtime and its version, run & build commands.

Reverse proxy configuration, Volume Configuration, Exposed Ports Configuration and Environment variables.

### Step 5: Choose Deployment Targets

Elestio provides two different types of deployment targets.

- New Infrastructure
- Existing Infrastructures

On elestio single CI/CD target you can deploy multiple CI/CD pipelines so, If you already have CI/CD target on elestio then you can deploy a new pipeline on the same existing CI/CD target by choosing **Existing Infrastructures** and then select the CI/CD target otherwise if you don't have anything or want to deploy on new target then you can choose **New Infrastructure**

If you choose **New Infrastructure** then you have to select the deployment mode we have two different types of deployment modes.

- Single-mode.
- Cluster mode.

  **NOTE:-** Steps 6,7,8 and 9 are only for New Infrastructure targets for Existing Infrastructures targets directly following the final step.

### Step 6: Select Service Cloud Provider

Elestio supports five different types of cloud service providers you can choose anyone to deploy your service.

- Hetzner Cloud.
- Digital Ocean.
- Amazon Lightsail.
- Linode.
- Vultr.

We also provide a BYOVM service option so if you already have your VM on any third-party provider (Azure, GCP, Alibaba, ...) then you can choose BYOVM to deploy CI/CD pipeline on your VM.

Elestio provides one BYOVM service for free. To be eligible the VM you connect must have no more than 2 vCPU, max 4 GB of ram, and max 80 GB of storage

### Step 7: Select Service Plan

This step is only for other than BYOVM service providers.

We're providing multiple different types of service plans as per proposing by your selected providers.

### Step 8: Provide Service Name

By default, we create a unique target name for you but you can customize it.

### Step Final: Create Ci/CD pipeline

Now after following all the above steps you can click on the button **Create Ci/CD pipeline**.

It will take a few seconds to deploy your pipeline on elestio.

For each pipeline deployed on elestio will create a cname for it. but if you want your custom domain then you can configure it inside the target details.

After Pipeline is deployed you can able to view the app by visiting the pipeline domain.