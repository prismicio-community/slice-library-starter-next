### **🚨⚠🚨 Storybook `6.0.x` Static Deployment Issue 🚨⚠🚨**

**Storybook `6.0.x` has an issue when building it static for deployment. This issue is preventing navigation between stories when visiting it, and is a known of Storybook ([storybookjs/storybook#11958](https://github.com/storybookjs/storybook/issues/11958)). Thankfully as of `11/19/2020` Storybook `6.1.0` [has been released](https://www.npmjs.com/package/@storybook/vue), fixing this bug.**

**This issue should not affect most of you as Slice Machine installs Storybook `5.x.x` by default. If you updated to Storybook `6.0.x`, update it again to Storybook `6.1.0` in order to fix this bug.**

**In any case regarding _#SliceContest_ if your deployed version of Storybook does not behave as it does in development mode (`$ yarn storybook`), have no worries, we will attempt to run it in development mode if we notice something is wrong.**

# Slice Library Next.js Starter [[#SliceContest: Slice Builder Release]](https://prismic.io/blog/slice-contest?utm_campaign=devexp&utm_source=github&utm_medium=slicecontestpost)

> Looking for the Vue.js counterpart? [Check out the Nuxt.js starter](https://github.com/prismicio-community/slice-library-starter-nuxt#readme).

A starter to create your slice library with [Next.js](https://nextjs.org) and [Slice Machine](https://slicemachine.dev) for [#SliceContest](https://prismic.io/blog/slice-contest?utm_campaign=devexp&utm_source=github&utm_medium=slicecontestpost). This document is here to help you through the whole process of creating your library but is not comprehensive to what you can do, unleash your creativity!

- [📚 &nbsp;Useful Links](#user-content--useful-links)
- [🏁 &nbsp;Getting Started](#user-content--getting-started)
  - [Setting up Your Project](#setting-up-your-project)
  - [Using the Prismic CLI](#using-the-prismic-cli)
  - [Setting up Prismic and Slice Machine](#setting-up-prismic-and-slice-machine)
- [👩‍💻 &nbsp;Developing](#user-content--developing)
  - [Creating a Slice](#creating-a-slice)
  - [Launching the Slice Builder](#launching-the-slice-builder)
- [🚀 &nbsp;Deploying Your Storybook](#user-content--deploying-your-storybook)
  - [Hosting on Netlify](#hosting-on-netlify)
  - [Hosting on Vercel](#hosting-on-vercel)
- [☑️ &nbsp;Submission Checklist](#user-content--submission-checklist)

## 📚 &nbsp;Useful Links

- [📣 &nbsp;Contest Announcement Blog Post](https://prismic.io/blog/slice-contest?utm_campaign=devexp&utm_source=github&utm_medium=slicecontestpost), check rules and additional information there!
- [🌐 &nbsp;Contest Forum Section](https://community.prismic.io/c/slice-machine/slicecontest), get help and share feedback here~
- [🔪 &nbsp;Slice Machine Documentation](https://www.slicemachine.dev/documentation), to learn more about Slice Machine
- [📖 &nbsp;Prismic React Documentation](https://prismic.io/docs/reactjs/getting-started/getting-started-from-scratch), to learn more about Prismic with React

## 🏁 &nbsp;Getting Started

Here's a step-by-step tutorial to get started using this starter.

### Setting up Your Project

Start by [forking this repository](https://github.com/prismicio-community/slice-library-starter-next/fork), this will create a copy of this repository on your GitHub account.

Once the repository is forked, you can clone it locally and install its dependencies:

```bash
$ git clone https://github.com/<your_username>/slice-library-starter-next
$ cd slice-library-starter-next
$ yarn install # if you use npm: `$ npm install`
```

While your package manager installs the dependencies, you can already update the [LICENSE](./LICENSE) file to replace `<copyright holders>` with your name. You can also update the [package.json](./package.json) file to fill the `author` field~

### Using the Prismic CLI

For convenience and to be sure you are running the correct version of Prismic CLI it has been installed as part of `devDependencies` and aliased to the `prismic` script in this project. Thanks to that you can run the CLI as a package script:

```bash
# Using Yarn
$ yarn prismic <command> <options>
# Using npm
$ npm run prismic -- <command> <options>
```

If you still wish to use the CLI installed globally make sure you are running version `3.8.3-beta.0` or greater:

```bash
# Installing the CLI globally using Yarn (optional)
$ yarn global add prismic-cli@3.8.3-beta.0
# Installing the CLI globally using npm (optional)
$ npm install --global prismic-cli@3.8.3-beta.0

# You can then use the CLI globally...
$ prismic <command> <options>
```

> In the following sections only the Yarn version from above (recommended) will be used in the examples for the sake of simplicity.

### Setting up Prismic and Slice Machine

If you do not own a Prismic account yet you can **create one** for free [here](https://prismic.io/dashboard/signup?redirectUri=/dashboard) or by using the CLI:

```bash
$ yarn prismic signup
# The CLI will then guide you through the process...
```

Once you have a Prismic account, or if you already had one, **log in** within the CLI:

```bash
$ yarn prismic login
# The CLI will then guide you through the process...
```

When logged in, you can then **bootstrap** your Slice Machine project, this will create you a Prismic repository for this project:

```bash
$ yarn prismic sm --bootstrap
# The CLI will then prompt you for a Prismic repository name...
```

Finally, and since that's a requirement for this contest, you will want to bootstrap a Storybook project. Thankfully Slice Machine comes with a handy command for that:

```bash
$ yarn prismic sm --add-storybook
```

This should create a simple Storybook inside your project. Bear in mind though that this one is still quite basic, feel free to go fancy by adding [addons](https://storybook.js.org/addons) and more! Here's an example of a more elaborated Storybook documentation of a slice library for inspiration: [sms-hoy-storybook.netlify.app](https://sms-hoy-storybook.netlify.app)

> ⚠ Storybook is known for being quite picky with its dependencies. If you experience a blank page when running it with a lot of errors in the browser console try deleting your lock file and installing dependencies again, should fix the issue.

Well done! You are now ready to start developing your slice library with Slice Machine.

## 👩‍💻 &nbsp;Developing

Some quick reminders to help you developing your library with Slice Machine and the Slice Builder. Please refer to the [documentation](https://www.slicemachine.dev/documentation) if you are looking for more in-depth knowledge.

### Creating a Slice

To create a slice run:

```bash
$ yarn prismic sm --create-slice
# The CLI will then guide you through the process...
```

This will create a new directory inside `./slices` named after the provided slice name. Inside it `index.js` is the slice component itself.

Slices behave just like any regular Next.js component but receives a `slice` prop containing its slice fields. You can install additional dependencies to the project like Tailwind CSS or Theme UI, although you might need to update the Storybook configuration and stories to reflect those.

For comprehensive documentation about creating your own slices check the dedicated [documentation](https://www.slicemachine.dev/documentation/create-your-own-slices-components).

### Launching the Slice Builder

To launch the Slice Builder you need to run 2 terminals: one for Storybook, one for the Slice Builder itself.

```bash
# On a first terminal
$ yarn storybook # or with npm: `$ npm run storybook`

# On the second terminal
$ yarn prismic sm --develop
```

This will launch Storybook on port `8888` and the Slice Builder on port `9999`, you can open a third terminal to create slices from or launch other commands...

> ℹ We are aware that it will be more convenient to launch Storybook and the Slice Builder with a single command and are working on it~

> ⚠ Storybook is known for being quite picky with its dependencies. If you experience a blank page when running it with a lot of errors in the browser console try deleting your lock file and installing dependencies again, should fix the issue.

> ⚠ We noticed that in some rare case you can get stuck in a `401 [Unauthorized]` loop prompting you to log in when running the Slice Machine develop command. If this happens to you check if your Prismic repository was created, if not, try running `$ yarn prismic login` and `$ yarn prismic sm --bootstrap` again.

For comprehensive documentation about using the Slice Builder check the dedicated [documentation](https://www.slicemachine.dev/documentation/slice-builder#using-the-slice-builder).

## 🚀 &nbsp;Deploying Your Storybook

One of the requirements of this contest if to have your Storybook documentation hosted somewhere.

If you are not familiar with hosting no worries! We recommend to either use [Netlify](https://netlify.com) **or** [Vercel](https://vercel.com) and have done most of the setup for you already!

You only need to host the documentation once, no need to have it at multiple location, so just pick one that works for you~

### Hosting on Netlify

To host your Storybook documentation on Netlify go to: [app.netlify.com/start](https://app.netlify.com/start), you might need to create an account or to log in if not already.

Once on the page click "**GitHub**". After granting access to your account you should now be able to see a list of your repositories. Pick the one you worked on.

On the last build options step every default should be good. We already took care of configuring the build command and publish directory through a [netlify.toml](https://docs.netlify.com/configure-builds/file-based-configuration/) file. Click "**Deploy site**" and wait for the magic to happen.

Once the build is finished, head over to the "**Site overview**" tab. The URL of the hosted documentation should be available at the top left of the tab (if Netlify is still building it will display you the build status instead). You can customize it by changing the site name under the "**Site settings**" tab.

Congratulations! You documentation is now hosted and will update itself whenever you commit to your repository.

### Hosting on Vercel

To host your Storybook documentation on Vercel go to: [vercel.com/import](https://vercel.com/import).

Once on the page click "**Continue**" under "**Import Git Repository**", you might need to create an account or to log in if not already.
After you logged in, paste the GitHub repository URL you worked on in the dedicated field and click "**Continue**", Vercel might ask for access to your account.

On the last build options step select "**Other**" under "**Framework Preset**", expand the "**Build and Output Settings**" options and set "**Output Directory**" to `out`. You can then click "**Deploy**" and wait for the magic to happen.

Once the build is finished and successful, you should be redirected to a success page. The URL of the hosted documentation should be available through the "**Visit**" button. You can customize it by changing the site name under the "**Settings**" tab of the new site dashboard.

Congratulations! You documentation is now hosted and will update itself whenever you commit to your repository.

## ☑️ &nbsp;Submission Checklist

To keep track of your progress and to be sure not to miss anything here's a simple checklist you can use. Once everything ticks you should be ready to submit your library to us by tagging [@prismicio](https://twitter.com/prismicio) with #SliceContest on Twitter.

- [ ] My library contains at least **5 different slices**
- [ ] I have updated the [LICENSE](./LICENSE) to credit myself for my library
- [ ] The Storybook documentation is hosted here: <!-- https://example.com -->
- [ ] My library does not contain any non-public licensed assets

> ☝️ For comprehensive rules refer to the contest [blog post](https://prismic.io/blog/slice-contest?utm_campaign=devexp&utm_source=github&utm_medium=slicecontestpost).
