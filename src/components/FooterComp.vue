<template>
  <footer class="footer mt-auto py-3 bg-light">
    <div class="container">
      <div class="row">
        <div class="col">
          <span class="text-muted"
            >This Webpage is created by Jiyoonholic.</span
          >
        </div>
        <div class="col"></div>
        <div class="col">
          <a href="mailto:jyholic1209@gmail.com" target="_blank">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="24"
              height="24"
              fill="currentColor"
              class="bi bi-mailbox2"
              viewBox="0 0 16 16"
            >
              <path
                d="M9 8.5h2.793l.853.854A.5.5 0 0 0 13 9.5h1a.5.5 0 0 0 .5-.5V8a.5.5 0 0 0-.5-.5H9v1z"
              />
              <path
                d="M12 3H4a4 4 0 0 0-4 4v6a1 1 0 0 0 1 1h14a1 1 0 0 0 1-1V7a4 4 0 0 0-4-4zM8 7a3.99 3.99 0 0 0-1.354-3H12a3 3 0 0 1 3 3v6H8V7zm-3.415.157C4.42 7.087 4.218 7 4 7c-.218 0-.42.086-.585.157C3.164 7.264 3 7.334 3 7a1 1 0 0 1 2 0c0 .334-.164.264-.415.157z"
              />
            </svg>
            &nbsp; to Jyholic</a
          >
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: "Footer-page",
};
</script>

<style scoped>
a {
  display: flex;
  text-align: end;
  justify-content: flex-end;
}
</style>
