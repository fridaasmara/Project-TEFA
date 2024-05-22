<template>
  <div class="row p-2 bg-primary text-white justify-content-center fixed-top">
    <div class="col-lg-1">
      <img src="~/assets/img/LOGO-SMK4.png" class="logo" alt="logo SMKN 4">
    </div>

    <div class="title col-lg-3">
      <h1>Perpus Digital</h1>
      <address>
        SMKN 4 Tasikmalaya
      </address>
    </div>
  </div>
</template>     

<style scoped>
.bg-primary {
  background-color: #748B95 !important;
  box-shadow: 1px 1px 10px #424242;
}

img {
  width: 90px;
}

h1 {
  font-weight: 600;
}

@media only screen and (max-width: 600px) {
  .row {
    text-align: center;
  }
  .logo {
    width: 50px;
  } 
  .title h1 {
    font-size: 25px;
  } 
  .title address {
    font-size: 15px;
  } 
}

@media only screen and (max-width: 890px) {
  .row {
    text-align: center;
  }
}

</style>