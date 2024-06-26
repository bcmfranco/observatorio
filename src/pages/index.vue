<style>

@import url("https://fonts.googleapis.com/css?family=Montserrat");

body {
  font-family: "Montserrat", sans-serif;
  background-color: #f8ecf5;
  margin: 0 auto;
  padding: 0;
  max-width: 700px;
}

header {
  background-color: #333;
  color: #fff;
  padding: 20px;
  text-align: center;
}

header h1 {
  font-size: 24px;
  font-weight: bold;
  margin: 0;
}

nav ul {
  list-style-type: none;
  padding: 0;
  display: flex;
  justify-content: center;
}

nav ul li {
  margin: 0 10px;
}

nav ul li a {
  color: #fff;
  text-decoration: none;
}

main {
  padding: 20px;
}

.blog-entries {
  display: grid;
  grid-template-columns: 1fr;
  grid-gap: 20px;
}

.entry {
  border: 1px solid #ccc;
  padding: 20px;
  border-radius: 5px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  background-color: rgb(241, 241, 241);
}

.entry h2 {
  margin-top: 0;
  font-size: 18px;
  font-weight: bold;
}

.tags {
  margin-top: 10px;
  display: flex;
  justify-content: flex-start;
  cursor: pointer;
}

.tag {
  background-color: #f2f2f2;
  padding: 5px 10px;
  border-radius: 3px;
  margin-right: 5px;
  font-size: 14px;
  border: 1px solid gray;
}

.tag:hover {
  background-color: #e5e5e5;
}

footer {
  background-color: #333;
  color: #fff;
  text-align: center;
  padding: 10px;
  clear: both;
}

footer p {
  font-size: 12px;
}

.menu-btn,
.close-btn,
#clean-btn {
  font-size: 24px;
  background-color: #333;
  color: #fff;
  padding: 10px 20px;
  border: none;
  cursor: pointer;
}

.nav {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.9);
  color: #fff;
  transform: translateY(-100%);
  transition: transform 0.5s ease;
}

.nav-open {
  transform: translateY(0);
}

.nav ul {
  list-style-type: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  font-size: 24px;
}

.nav li {
  line-height: 30px;
  padding: 5px 10px;
  cursor: pointer;
}

.tag {
  background-color: #f2f2f2;
  padding: 5px 10px;
  border-radius: 3px;
  margin-right: 5px;
  font-size: 14px;
}

.tag:hover {
  background-color: #e5e5e5;
}

.close-btn {
  position: absolute;
  top: 10px;
  right: 10px;
  background-color: #333;
  color: #fff;
  padding: 5px 10px;
  border: none;
  cursor: pointer;
}

#clean_tags{
  font-size: 24px;
  background-color: #333;
  color: #fff;
  padding: 10px 20px;
  border: none;
}


</style>

<template>
  <h1>Lo que aprendí</h1>
  
  <button class="menu-btn" @click="toggleMenu" :aria-expanded="menuOpen">Tags</button>
  
  <nav class="nav" :class="{ 'nav-open': menuOpen }" :aria-hidden="menuOpen" @click.self="toggleMenu">
    <button class="close-btn" @click="toggleMenu">Cerrar</button>
    <ul>
      <li v-for="tag in tags" :key="tag" @click="filterByTag(tag)">{{ tag }}</li>
      <li id="clean-btn" @click="clearFilter">Limpiar</li>
    </ul>
  </nav>
  
  <div class="blog-entries">
    <article class="entry" v-for="entry in filteredEntries" :key="entry.id">
      <p>{{ entry.content }}</p>
      <div class="tags">
        <span class="tag" v-for="tag in entry.tags" :key="tag" @click="filterByTag(tag)">{{ tag }}</span>
      </div>
    </article>
  </div>
</template>

<script>

import contentData from '../entries.json'

export default {
  data() {
    return {
    menuOpen: false,
    tags: Array.from(new Set(contentData.flatMap(entry => entry.tags))),
    entries: contentData,
    selectedTag: null
  }
},
  computed: {
    filteredEntries() {
      if (this.selectedTag) {
        return this.entries.filter(entry => entry.tags.includes(this.selectedTag));
      } else {
        return this.entries;
      }
    }
  },
  methods: {
    toggleMenu() {
      this.menuOpen = !this.menuOpen;
    },
    filterByTag(tag) {
      this.selectedTag = tag;
      this.toggleMenu();
    },
    clearFilter() {
      this.selectedTag = null;
      this.toggleMenu();
    }
  },
}
</script>