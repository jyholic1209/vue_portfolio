<template>
  <HeaderComp />
  <body class="d-flex h-100 text-center text-white bg-dark">
    <div class="cover-container d-flex w-100 h-100 p-3 mx-auto flex-column">
      <main class="px-3">
        <h1>Web Project Portfolio</h1>
        <p class="lead">This is Vue3 Web Application Project by Jyholic.</p>
        <p class="lead">
        
        </p>
        <p class="lead">
          <ul>
            <li> Vue3 Programming {{ getStudyVueDay() }} Hours</li>
          </ul>
          <a
            href="#"
            class="btn btn-lg btn-secondary fw-bold border-white bg-white"
            >Learn more</a
          >
        </p>
      </main>
    </div>
    <hr>
  </body>
  <DetailPage v-bind:title="'WebCam Control'" />
  <WebCamPage />
    
  <FooterComp />
</template>

<script>
import HeaderComp from "./components/HeaderComp.vue";
import FooterComp from "./components/FooterComp.vue";
import moment from "moment";
import DetailPage from "./components/DetailPage.vue";
import WebCamPage from "./components/WebCamPage.vue";

export default {
  name: "App",
  components: { HeaderComp, FooterComp, DetailPage, WebCamPage },
  data() {
    return {
      
  };
  },
  computed : {
    },
  methods: {
    getStudyVueDay() {
      const nowDate = new moment();
      const stDate = new moment([2022, 8, 8]);
      return stDate.diff(nowDate,'hours');
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
