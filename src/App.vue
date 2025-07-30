<script setup>
import { reactive, ref, computed } from 'vue';

// const BookAuthor = ref(true);

const author = reactive({
  name: 'James Gun',
  books: [
    {
      title: 'The Alchemist 1',
      author: 'Paulo Coelho',
      releaseDate: '2022',
      reviews: [
        'A great book about following your dreams.',
        'what a great book',
        'it is a very good book',
      ],
    },
    {
      title: 'The Alchemist 2',
      author: 'Paulo Coelho',
      releaseDate: '2024',
      reviews: ['A great book about life.', 'it change your life', 'the next level book'],
    },
  ],
});

const isPublished = computed(() => {
  return author.books.length > 0 ? 'Published Yes' : 'Published No';
});

const count = ref(0);

const increment = () => {
  count.value++;
};
</script>

<template>
  {{ isPublished }}
  <button @click="increment">{{ count }}</button>

  <h1>
    {{ author.name }}
    <span v-if="author.books.length === 1">Published a book</span>
    <span v-else-if="author.books.length > 1">Published many books</span>
    <span v-else>Published No books</span>
  </h1>

  <h2>
    <ul>
      <li v-for="({ title, releaseDate, reviews }, index) in author.books" :key="`book-${index}`">
        {{ title }} - {{ releaseDate }}
        <span v-for="(review, reviewIndex) in reviews" :key="`review-${reviewIndex}`">{{
          review
        }}</span>
      </li>
    </ul>
  </h2>
</template>

<style scoped></style>
