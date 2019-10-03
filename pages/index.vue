<template>
  <section class="container">
    <Navigation :books='navItems' />
    <div class="container__content">
      <h1>Please select a book you wish to view</h1>
      <p>This is a website for demo purposes of using Nuxt & Contentful together</p>
    </div>
  </section>
</template>

<script>
  import Navigation from '../components/Navigation';
  import { createClient } from '../plugins/contentful';
const contentfulClient = createClient();
  export default {
    components: {
      Navigation
    },
    asyncData ({env}) {
      return Promise.all([
        // fetch all blog posts sorted by creation date
        contentfulClient.getEntries({
          'content_type': 'book',
          order: '-sys.createdAt'
        })
      ]).then(([books]) => {
        // return data that should be available
        // in the template
        return {
          navItems: books.items
        }
      }).catch(console.error)
}
  }
</script>




<!--template>
  <section class="container">
    <div>
      <app-logo/>
      <h1 class="title">
        nuxt-contentful-demo
      </h1>
      <h2 class="subtitle">
        Nuxt.js project
      </h2>
      <div class="links">
        <a
          href="https://nuxtjs.org/"
          target="_blank"
          class="button--green">Documentation</a>
        <a
          href="https://github.com/nuxt/nuxt.js"
          target="_blank"
          class="button--grey">GitHub</a>
      </div>
    </div>
  </section>
</template>

<script>
import AppLogo from '~/components/AppLogo.vue'

export default {
  components: {
    AppLogo
  }
}
</script>

<style>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif; /* 1 */
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style-->





