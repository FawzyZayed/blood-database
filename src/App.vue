<template>
  <div>
    <b-container class="my-5">
      <b-navbar toggleable="lg" type="light" variant="info">
        <b-navbar-brand href="/">Boold DataBase</b-navbar-brand>
        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
        <b-collapse id="nav-collapse" is-nav>
          <!-- Right aligned nav items -->
          <b-navbar-nav class="ml-auto">
            <b-navbar-nav right>
              <router-link :to="{name : 'home'}" tag="li" class="nav-item"><a class="nav-link">Home</a></router-link>
              <router-link :to="{name : 'donate'}" tag="li" class="nav-item"><a class="nav-link">Donate</a></router-link>
              <router-link :to="{name: 'about'}" tag="li" class="nav-item"><a class="nav-link">About</a></router-link>
            </b-navbar-nav>
          </b-navbar-nav>
        </b-collapse>
      </b-navbar>
    </b-container>
    <b-container class="mb-5">
      <router-view></router-view>
    </b-container>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'App',
  data: () => ({
    //
  })
})
</script>
