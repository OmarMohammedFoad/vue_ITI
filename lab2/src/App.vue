<script setup>
import { ref } from 'vue';
import BookCard from './components/Books.vue';
import { booksData } from './assets/data';

const allBooks = ref(booksData);
const items = ref([]);
const shownBooks = ref(false);
const shownItems = ref(false);

const showBooks = () => {
  shownBooks.value = !shownBooks.value;
  if (shownBooks.value) {
    shownItems.value = false;
  }
};

const showItems = () => {
  shownItems.value = !shownItems.value;
  if (shownItems.value) {
    shownBooks.value = false;
  }
};

const addToItems = (book) => {
  const exists = items.value.find(item => item.ISBN === book.ISBN);
  if (!exists) {
    items.value.push(book);
  }
};

const removeFromItems = (book) => {
  const index = items.value.findIndex(item => item.ISBN === book.ISBN);
  if (index > -1) {
    items.value.splice(index, 1);
  }
};
</script>

<template>
  <div class="bg-gray-100 min-h-screen p-10 text-center">
    <div class="flex flex-col items-center h-full overflow-y-auto">
      <!-- Navigation Buttons -->
      <div class="flex gap-4 mb-6">
        <button @click="showBooks" class="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600 transition-colors">
          {{ shownBooks ? 'Hide Books' : 'Show Books' }}
        </button>
        <button @click="showItems" class="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600 transition-colors">
          {{ shownItems ? 'Hide List' : 'Show List' }} ({{ items.length }})
        </button>
      </div>

      <!-- Books Grid -->
      <div v-if="shownBooks" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 mb-10">
        <BookCard v-for="book in allBooks" :key="book.ISBN" :book="book" button-text="Add" button-action="add"
          @action="addToItems" />
      </div>

      <!-- Selected Items Grid -->
      <div v-if="shownItems" class="w-full">
        <h2 class="text-2xl font-bold mb-4">Selected Books</h2>
        <div v-if="items.length > 0" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
          <BookCard v-for="item in items" :key="`selected-${item.ISBN}`" :book="item" button-text="Remove"
            button-action="remove" @action="removeFromItems" />
        </div>
        <div v-else class="text-gray-500 text-lg">
          No books selected yet. Add some books from the catalog!
        </div>
      </div>

      <!-- Welcome Message -->
      <div v-if="!shownBooks && !shownItems" class="text-center py-20">
        <h1 class="text-4xl font-bold text-gray-800 mb-4">Book Management System</h1>
        <p class="text-xl text-gray-600 mb-8">Discover and manage your favorite books</p>
        <div class="space-y-4">
          <p class="text-gray-500">Click "Show Books" to browse our catalog</p>
          <p class="text-gray-500">Click "Show List" to view your selected books</p>
        </div>
      </div>
    </div>
  </div>
</template>
