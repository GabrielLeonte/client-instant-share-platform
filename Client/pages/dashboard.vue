<template>
    <div>
        Hi
    </div>
</template>

<script>
import { mapGetters } from 'vuex'
export default {
    middleware: ['auth','admin'],
     computed: {
       ...mapGetters(['isAuthenticated', 'loggedInUser','isAdmin'])
     }
}
</script>
