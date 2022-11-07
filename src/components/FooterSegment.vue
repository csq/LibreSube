<template>
<link href="https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css" rel="stylesheet"/>
<footer class="footer mt-auto">
  <div class="container p-1">
    <div class="row">
      <div class="col">
        <a href="https://github.com/csq/libre-sube/" target="_blank"><i class="fa fa-github"></i></a>
        <a href="mailto:carlos.quiroz.90@gmail.com"><i class="fa fa-envelope-o"></i></a>
      </div>
    </div>
  </div>
</footer>
</template>

<style scoped>
@media screen and (max-width: 480px) {
  .footer {
    padding-right: 2%;
    padding-left: 2%;
  }
}
.footer {
  background: #333333;
  text-align: center;
}

.footer a {
  color: #ffffff;
  font-size: large;
  padding-left: 1em;
  padding-right: 1em;
  transition: all .5s ease;
}

.footer a:hover {
  color: #0e8ccc;
}
</style>