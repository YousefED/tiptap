---
title: Vue.js 2 WYSIWYG
tableOfContents: true
---

# Vue.js 2

## Introduction
The following guide describes how to integrate Tiptap with your [Vue](https://vuejs.org/) CLI project.

## Requirements
* [Node](https://nodejs.org/en/download/) installed on your machine
* [Vue CLI](https://cli.vuejs.org/) installed on your machine
* Experience with [Vue](https://vuejs.org/v2/guide/#Getting-Started)

## 1. Create a project (optional)
If you already have an existing Vue project, that’s fine too. Just skip this step and proceed with the next step.

For the sake of this guide, let’s start with a fresh Vue project called `tiptap-example`. The Vue CLI sets up everything we need, just select the default Vue 2 template.

```bash
# create a project
vue create Tiptap-example

# change directory
cd Tiptap-example
```

## 2. Install the dependencies
Okay, enough of the boring boilerplate work. Let’s finally install Tiptap! For the following example you’ll need the `@tiptap/vue-2` package, with a few components, and `@tiptap/starter-kit` which has the most common extensions to get started quickly.

```bash
# install with npm
npm install @tiptap/vue-2 @tiptap/starter-kit

# install with Yarn
yarn add @tiptap/vue-2 @tiptap/starter-kit
```

If you followed step 1 and 2, you can now start your project with `npm run dev` or `yarn dev`, and open [http://localhost:8080](http://localhost:8080) in your favorite browser. This might be different, if you’re working with an existing project.

## 3. Create a new component
To actually start using Tiptap, you’ll need to add a new component to your app. Let’s call it `Tiptap` and put the following example code in `components/Tiptap.vue`.

This is the fastest way to get Tiptap up and running with Vue. It will give you a very basic version of Tiptap, without any buttons. No worries, you will be able to add more functionality soon.

```html
<template>
  <editor-content :editor="editor" />
</template>

<script>
import { Editor, EditorContent } from '@tiptap/vue-2'
import StarterKit from '@tiptap/starter-kit'

export default {
  components: {
    EditorContent,
  },

  data() {
    return {
      editor: null,
    }
  },

  mounted() {
    this.editor = new Editor({
      content: '<p>I’m running Tiptap with Vue.js. 🎉</p>',
      extensions: [
        StarterKit,
      ],
    })
  },

  beforeDestroy() {
    this.editor.destroy()
  },
}
</script>
```

## 4. Add it to your app
Now, let’s replace the content of `src/App.vue` with the following example code to use our new `Tiptap` component in our app.

```html
<template>
  <div id="app">
    <tiptap />
  </div>
</template>

<script>
import Tiptap from './components/Tiptap.vue'

export default {
  name: 'App',
  components: {
    Tiptap
  }
}
</script>
```

You should now see Tiptap in your browser. Time to give yourself a pat on the back! :)

## 5. Use v-model (optional)
You’re probably used to bind your data with `v-model` in forms, that’s also possible with Tiptap. Here is a working example component, that you can integrate in your project:

https://embed.tiptap.dev/preview/GuideGettingStarted/VModel