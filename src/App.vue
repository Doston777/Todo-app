<template>
  <div id="app">
    <link rel="stylesheet" href="">
    <div id="nav">
      <router-link to='/'>Home</router-link>|
      <router-link to='/about'>About</router-link>
    </div>
    <router-view />
  </div>
</template>

<style>
  #nav {
    padding: 30px;
    text-align: center;
    background-color: navy;
  }

  #nav a {
    font-weight: bold;
    color: #2c3e;
  }

  #nav a.router-link-exact-active {
    color: #2c3e;
  }
</style>