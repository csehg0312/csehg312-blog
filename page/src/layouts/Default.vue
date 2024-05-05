<template>
  <div class="layout">
    <header class="header">
      <strong>
        <g-link to="/" style="color: #1a1a1a; text-decoration: none; border-radius: 4em; border-color:#1a1a1a">{{ $static.metadata.siteName }}</g-link>
      </strong>
      <nav :class="{'open': isNavOpen}">
        <!-- <button class="nav-toggle" @click="toggleNav">☰</button> -->
        <div class="nav__links">
          <g-link class="nav__link" to="/">Otthon</g-link>
          <g-link class="nav__link" to="/about/">Rólam</g-link>
          <g-link class="nav__link" to="/poetry/">Versek</g-link>
          <g-link class="nav__link" to="/projects/">Projektek</g-link>
        </div>
      </nav>
    </header>
    <slot/>
  </div>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>

<script>

export default {
  data() {
    return {
      isNavOpen:false
    };
  },
  methods: {
    toggleNav() {
      this.isNavOpen = !this.isNavOpen;
    }
  }
}

</script>

<style>
body {
  font-family: -apple-system,system-ui,BlinkMacSystemFont,"Segoe UI",Roboto,"Helvetica Neue",Arial,sans-serif;
  margin:0;
  padding:0;
  line-height: 1.5;
}

.layout {
  max-width: 760px;
  margin: 0 auto;
  padding-left: 20px;
  padding-right: 20px;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
  height: 80px;
}

@keyframes fillAnimation {
  from {
    background-position: bottom;
    background-color: #f9f9f9;
    color: #1a1a1a;
  }
  to {
    background-position: top;
    background-color: #1a1a1a;
    color: #f9f9f9;
  }
}
.nav-links {
  display: none;
}

.nav-links.open {
  display: block;
}


.nav__link {
  margin-left: 20px;
  color: #1a1a1a;
  text-decoration: none;
  border-radius:0.1em;
  border-width: 0.3em;
  border-color: #1a1a1a;
  border-style: solid;
  padding: 0.5em;
  background: linear-gradient(to top, #f9f9f9 50%, transparent 50%); 
  background-size: 100% 200%; 
}

.nav__link:hover {
  /* background-position: top; */
  animation: fillAnimation 1s forwards;
}

.nav__link::after {
  animation: fillAnimation 3s backwards;
}

@media only screen and (max-width: 767px) {
  .nav__link{
    margin-left: 10px;
    font-size: 14px;
  }
}
</style>
