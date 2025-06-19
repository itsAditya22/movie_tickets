<template>
    <div class="container mx-auto px-4 py-8">
        <h1 class="text-3xl font-semibold text-gray-800 mb-4">List of Movies</h1>

        <ul v-if="movies.data" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
            <li v-for="movie in movies.data" :key="movie.id" class="bg-white rounded-lg shadow-md overflow-hidden">
                <router-link :to="{ name: 'MovieDetails', params: { movieName: movie.name } }" class="block hover:bg-gray-100 transition duration-300">
                    <img :src="movie.poster" class="w-full h-48 object-cover">
                    <div class="px-4 py-2">
                        <h2 class="text-lg font-semibold text-gray-800">{{ movie.title }}</h2>
                    </div>
                </router-link>
            </li>
        </ul>
    </div>
</template>

<script setup>
import { createListResource } from 'frappe-ui';

const movies = createListResource({
    doctype: 'Movie',
    fields: ['name', 'title', 'release_date', 'director', 'poster'],
    auto: true,
});
</script>