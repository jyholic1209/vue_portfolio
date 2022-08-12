<template>
  <HeaderComp />
  <body class="d-flex h-100 text-center text-white bg-dark">
    <div class="cover-container d-flex w-100 h-100 p-3 mx-auto flex-column">
      <main class="px-3">
        <h1>Web Project Portfolio</h1>
        <p class="lead">This is Vue3 Web Application Project by Jyholic.</p>
        <p class="lead">
          {{ getStudyVueDay()}}
        </p>
        <p class="lead">
          <ul>
            <li></li>
          </ul>
          <a
            href="#"
            class="btn btn-lg btn-secondary fw-bold border-white bg-white"
            >Learn more</a
          >
        </p>
      </main>
    </div>
  </body>
  <FooterComp />
</template>

<script>
import HeaderComp from "./components/HeaderComp.vue";
import FooterComp from "./components/FooterComp.vue";

export default {
  name: "App",
  components: { HeaderComp, FooterComp },
  data() {
    return {
      startDate: new Date(2022,8,8),
  };
  },
  methods: {
    getStudyVueDay() {
      const nowDate = new Date();
      console.log(nowDate,"현재");
      console.log(`start ${this.startDate}`)
      return nowDate - this.startDate;
    },
  },
};
</script>

<style scoped src="./assets/style.css">
.bd-placeholder-img {
  font-size: 1.125rem;
  text-anchor: middle;
  -webkit-user-select: none;
  -moz-user-select: none;
  user-select: none;
}

@media (min-width: 768px) {
  .bd-placeholder-img-lg {
    font-size: 3.5rem;
  }
}
</style>
