<!-- ./app.vue -->

<template>
    <div>
        <h1>My blog site</h1>
        <ul>
            <li :data="article" v-for="(article, index) in articles" :key="article._id">

                <!--
                  Add a link to each article title and
                  include the article slug in the path
                 -->
                <nuxt-link :to="`/${article._slug}`">
                    {{ article.title }}
                </nuxt-link>

            </li>
        </ul>
    </div>
</template>

<script setup>

import { GetArticles } from "@/queries/get-articles";

const { data } = await useAsyncQuery(GetArticles);
const articles = data.value.Articles.items;

console.log(JSON.stringify(articles, undefined, 2));

</script>
