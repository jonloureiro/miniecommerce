<template lang="html">
  <header :class="$options.name">
    <nav :class="`${$options.name}__nav`">
      <router-link :class="`${$options.name}__link`" to="/">
        <h2 :class="`${$options.name}__title`">{{ title }}</h2>
      </router-link>
      <router-link :class="`${$options.name}__link`" to="/about">
        About
      </router-link>
      <router-link v-if="!hasUser" :class="`${$options.name}__link`" to="/login">
        Login
      </router-link>
      <router-link v-else :class="`${$options.name}__link`" to="/profile">
        Profile
      </router-link>
    </nav>
  </header>
</template>

<script>
module.exports = {
  name: 'Bar',
  data: function() {
    return {
      title: 'Title Page'
    }
  },
  computed: {
    hasUser: function() {
      return this.$store.state.user.on;
    }
  }
}
</script>

<style lang="css" scoped>
.Bar {
  padding-left: 2rem;
  padding-right: 2rem;
  background-color: #556270
  /* background: linear-gradient(to left, #556270, #d18181); */
}

.Bar__nav {
  display: grid;
  grid-template-columns: minmax(50%, 100%) repeat(2, 6rem);
  align-items: center;
  justify-items: center;
  height: 100%
}

.Bar__title {
  margin: 0px;
}

.Bar__link:first-child {
  justify-self: start;
}

.Bar__link {
  color: #EFF0F2;
  text-decoration: none;
}
</style>
