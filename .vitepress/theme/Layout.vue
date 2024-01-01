<script setup lang="ts">
import { useData } from 'vitepress'
import { data as archives } from '../../archives.data.ts'

const { site, frontmatter } = useData()
</script>

<template>
  <header>
    <h1>
      <a href="/">
        <img src="/logo.png" :alt="site.title">
      </a>
    </h1>
    <p>{{ site.description }}</p>
  </header>
  <nav>
    <a href="/">ホーム</a>
    <a href="/about">水珈琲の日誌について</a>
    <a href="/recommended">おすすめ記事</a>
    <a href="/privacy-policy">プライバシーポリシー</a>
  </nav>
  <div v-if="frontmatter.home">
    <ul>
      <li v-for="post of archives">
        <a :href="post.url">{{ post.frontmatter.title }}</a>
        <span>by {{ post.frontmatter.author }}</span>
      </li>
    </ul>
  </div>
  <div v-else>
    <a href="/">Home</a>
    <Content />
  </div>
</template>
