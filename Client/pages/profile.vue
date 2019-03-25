<template>
  <section class="section light-text">
    <div class="container">
      <h2 class="title light-text">My Profile</h2>
      <div class="content">
        <p>
          <strong class="light-text">Username:</strong>
          {{ loggedInUser.username }}
        </p>
        <p>
          <strong class="light-text">Data:</strong>
          {{ loggedInUser }}
        </p>
      </div>
    </div>
  </section>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
middleware: 'auth',
  computed: {
    ...mapGetters(['loggedInUser'])
  }
}
</script>