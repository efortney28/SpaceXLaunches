<template>
  <div id="app">
    <div id="nav">
      <router-link tag="li" to="/"><a>Upcoming</a></router-link>
      <router-link tag="li" to="/previous"><a>Previous</a></router-link>
    </div>
    <router-view/>
  </div>
</template>

<style>
body {
  margin: 1em;
}
li {
  display: inline;
  margin: 1em;

}
li:hover {
  text-decoration: none;
}
</style>
