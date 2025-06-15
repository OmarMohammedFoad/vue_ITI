<script setup>
const props = defineProps({
    book: Object,
    buttonText: String,
    buttonAction: {
        type: String,
        validator: value => ['add', 'remove'].includes(value)
    }
});

const emit = defineEmits(['action']);

const handleAction = () => {
    emit('action', props.book);
};
</script>

<template>
    <div class="bg-white p-4 rounded shadow w-72">
        <img :src="book.image" :alt="`${book.Name} cover`" class="h-48 w-full object-cover rounded mb-2" />
        <h2 class="text-xl font-bold">{{ book.Name }}</h2>
        <p class="text-gray-700">{{ book.author }}</p>
        <p class="text-sm text-gray-500">{{ book.category }} - {{ book.numberofpage }} pages</p>
        <p class="text-green-600 font-semibold mt-1">{{ book.price }} EGP</p>
        <button @click="handleAction" :class="[
            'px-4 py-2 rounded text-white transition-colors',
            buttonAction === 'add'
                ? 'bg-red-500 hover:bg-red-600'
                : 'bg-red-500 hover:bg-red-600'
        ]">
            {{ buttonText }}
        </button>
    </div>
</template>
