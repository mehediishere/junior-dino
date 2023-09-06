// App.vue
// assets folder is inside `src` folder

<script setup>
  import "https://code.jquery.com/jquery-3.4.1.min.js";
  import "https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/js/bootstrap.bundle.min.js";
  import "@/assets/lib/easing/easing.min.js";
  import "@/assets/lib/owlcarousel/owl.carousel.min.js";
  import "@/assets/mail/jqBootstrapValidation.min.js";
  import "@/assets/mail/contact.js";
  import "@/assets/js/main.js";

  $(function (){
    alert("Hell There!");
  });
</script>

<template>
  <p class="text-danger">Hello</p>
</template>

<style scoped>
  @import url("https://fonts.googleapis.com/css2?family=Poppins:wght@100;200;300;400;500;600;700;800;900&display=swap");
  @import url("https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.10.0/css/all.min.css");
  @import "assets/lib/owlcarousel/assets/owl.carousel.min.css";
  @import "assets/css/style.css";
</style>
