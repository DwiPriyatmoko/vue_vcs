<script setup>
import { reactive, ref, computed } from 'vue';
import MainButton from './components/MainButton.vue';

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

const authorTwo = reactive({
  name: 'Fred Smith',
  books: [
    {
      title: 'The Journey 1',
      releaseDate: '2002',
      reviews: [4, 5, 4],
      avgReview: 4,
    },
    {
      title: 'The Journey 2',
      releaseDate: '2004',
      reviews: [7, 8, 9],
      avgReview: 8,
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

  <h2>Books:</h2>
  <ul>
    <li v-for="({ title, releaseDate, reviews }, index) of authorTwo.books" :key="`book-${index}`">
      {{ title }} - {{ releaseDate }}
      <span v-for="(review, reviewIndex) in reviews" :key="`review-${reviewIndex}`">
        {{ review }}</span
      >
    </li>
  </ul>

  <ul>
    <li v-for="(value, key, index) in authorTwo" :key="key">
      {{ index }} <b>{{ value }}</b> {{ key }}
    </li>
  </ul>

  <ol>
    <li v-for="(item, index) in 10" :key="index">My name - {{ item }}</li>
  </ol>

  <ul>
    <template v-for="(item, index) in authorTwo.books" :key="index">
      <MainButton v-if="item.avgReview > 5" :title="item.title" />
    </template>
  </ul>
</template>

<style scoped></style>
