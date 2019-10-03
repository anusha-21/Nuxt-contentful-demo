// Navigation.vue
<template>
    <div class="navigation">
      <nav>
        <ul role="menu">
          <li v-for="(navItem, index) in books" :key="index">
            <nuxt-link :to="'/' + navItem.fields.bookId" role="menuitem">{{navItem.fields.title}}</nuxt-link>
          </li>
        </ul>
      </nav>
    </div>
</template>

<script>
    export default {
        name: 'Navigation',
        props: {
          books: {
            type: Array, // We expect an array of books that we need for our navigation
            required: true
          }
        }
    }
</script>