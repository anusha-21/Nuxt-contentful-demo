<template>
  <div class="book-component">
    <a @click="$router.go(-1)">Go back to overview</a>
    <hr />
    <h1>Writer: {{book.fields.writer}}</h1>
    <!-- <img :src="book.fields.image.fields.file.url" :alt="book.fields.heading" v-if="book.fields.image" /> -->
    <p>
      {{book.fields.content}}
    </p>
  </div>
</template>

<script>
  import {createClient} from '../../plugins/contentful';
  const contentfulClient = createClient();

  export default {
    name: 'index',
    asyncData ({ env, params }) {
      return contentfulClient.getEntries({
        'content_type': 'book',
        'fields.bookId': params.id
      }).then(book => {
        return {
          book: book.items[0]
        }
      }).catch(console.error)
    }
  }
</script>