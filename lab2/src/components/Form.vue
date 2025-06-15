<script>
export default {
  data() {
    return {
      title: '',
      content: '',
      category: '',
      series: '',
      shareOn: '',
      submitted: false,
      formData: {}
    };
  },
  methods: {
    submitForm() {
      this.formData = {
        title: this.title,
        content: this.content,
        category: this.category,
        series: this.series,
        shareOn: this.shareOn
      };
      this.submitted = true;
    }
  }
};
</script>

<template>
  <div class="max-w-xl mx-auto bg-black p-6 rounded shadow mt-10 text-white">
    <h2 class="text-2xl font-bold mb-4">Article Form</h2>

    <div class="mb-4">
      <label class="block font-semibold mb-1">Title</label>
      <input v-model="title" type="text" class="input input-bordered w-full text-black" />
    </div>

    <div class="mb-4">
      <label class="block font-semibold mb-1">Content</label>
      <textarea v-model="content" rows="4" class="textarea textarea-bordered w-full text-black"></textarea>
    </div>

    <div class="mb-4">
      <label class="block font-semibold mb-1">Category</label>
      <div class="flex gap-4">
        <label><input type="radio" value="Testing" v-model="category" /> Testing</label>
        <label><input type="radio" value="Developing" v-model="category" /> Developing</label>
        <label><input type="radio" value="Design" v-model="category" /> Design</label>
      </div>
    </div>

    <div class="mb-4">
      <label class="block font-semibold mb-1">Series</label>
      <select v-model="series" class="select select-bordered w-full text-black">
        <option disabled value="">Choose a series</option>
        <option>Vue Basics</option>
        <option>Advanced Vue</option>
        <option>UI Design</option>
      </select>
    </div>

    <div class="mb-4">
      <label class="block font-semibold mb-1">Share On</label>
      <div class="flex gap-4">
        <label><input type="radio" value="Facebook" v-model="shareOn" /> Facebook</label>
        <label><input type="radio" value="LinkedIn" v-model="shareOn" /> LinkedIn</label>
        <label><input type="radio" value="Twitter" v-model="shareOn" /> Twitter</label>
      </div>
    </div>

    <button @click="submitForm" class="btn btn-primary w-full mt-4">Submit</button>

    <div v-if="submitted" class="mt-8 bg-gray-100 p-4 rounded shadow text-black">
      <h3 class="text-xl font-bold mb-2">Submitted Data:</h3>
      <p><strong>Title:</strong> {{ formData.title }}</p>
      <p><strong>Content:</strong> {{ formData.content }}</p>
      <p><strong>Category:</strong> {{ formData.category }}</p>
      <p><strong>Series:</strong> {{ formData.series }}</p>
      <p><strong>Share On:</strong> {{ formData.shareOn }}</p>
    </div>
  </div>
</template>

<style scoped>
/* Optional styles */
</style>
