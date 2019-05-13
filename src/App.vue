<template>
  <div id="app">
    <div class="container-fluid">
      <nav class="navbar sticky-top navbar-dark bg-dark">
        <span class="navbar-brand">SpaceX Launch Library</span>
        <div class="float-right">
          <router-link tag="li" to="/" class="nav-item"><a>Upcoming</a></router-link>
          <router-link tag="li" to="/previous"><a>Previous</a></router-link>
        </div>
      </nav>
    </div>
    <div class="container">
      <router-view/>
    </div>
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
}
div.container-fluid {
  margin: 0;
  padding: 0;
}
li {
  display: inline;
  margin: 0 1em;
}
a {
  color: #ccc;
}
a:hover {
  text-decoration: none;
  color: coral;
}
</style>
