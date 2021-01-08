<template>
  <div id="app">
    <div v-if="loader" class="container-fluid d-flex justify-content-center align-items-center loader-container">
      <div class="sk-cube-grid">
      <div class="sk-cube sk-cube1"></div>
      <div class="sk-cube sk-cube2"></div>
      <div class="sk-cube sk-cube3"></div>
      <div class="sk-cube sk-cube4"></div>
      <div class="sk-cube sk-cube5"></div>
      <div class="sk-cube sk-cube6"></div>
      <div class="sk-cube sk-cube7"></div>
      <div class="sk-cube sk-cube8"></div>
      <div class="sk-cube sk-cube9"></div>

    </div>
    </div>
    
    <div v-if="content" class="container-fluid p-0 text-center">
      <div>
        <div class="bg-left"></div>
        <div class="bg-right"></div>
      </div>

      <h2 class="heading">{{ names }}</h2>

      <img class="shadow-lg image1 " src="./assets/image1.jpg" alt="" />

      <div class="text-lg-end d-flex d-lg-block justify-content-center w-100 socials ">
        <div>
          <a target="_blank" :href="instagram" class="fa fa-instagram"></a>
        </div>
        <div>
          <a target="_blank" :href="twitter" class="fa fa-twitter-square"></a>
        </div>
        <div>
          <a target="_blank" :href="snapchat" class="fa fa-snapchat-square"></a>
        </div>
        <div>
          <a target="_blank" :href="mail" class="fa fa-envelope-square"></a>
        </div>
      </div>

      <nav class="navbar navbar-expand-md ">
        <div class="container-fluid">
          <button
            class="navbar-toggler"
            type="button"
            data-bs-toggle="collapse"
            data-bs-target="#navbarNavAltMarkup"
            aria-controls="navbarNavAltMarkup"
            aria-expanded="false"
            aria-label="Toggle navigation"
          >
            <i class="fa fa-bars text-white"></i>
          </button>
          <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
            <div class="navbar-nav">
              <a class="nav-link my-auto" href="#">HOME</a>
              <a class="nav-link my-auto" href="#">ABOUT</a>
              <span class="nav-link d-none d-md-block" 
                ><img src="./assets/image2.jpg" alt=""
              /></span>
              <a class="nav-link my-auto" href="#">GALLERY</a>
              <a class="nav-link my-auto" href="#">CONTACT</a>
            </div>
          </div>
        </div>
      </nav>

     
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      names: "",
      twitter: "",
      instagram: "",
      snapchat: "",
      email: "",
      loader: true,
      content: false
    };
  },
  created() {

    this.$http.get("https://hirng-x2021.glitch.me/api").then(function (data) {
      this.names = data.body.name;
      this.twitter = "https://twitter.com/" + data.body.social_media.twitter;
      this.instagram =
        "https://instagram.com/" + data.body.social_media.instagram;
      this.snapchat =
        "https://www.snapchat.com/add/" + data.body.social_media.snapchat;
      this.mail = "mailto:" + data.body.social_media.mail;
    });
  },
  mounted(){
    setTimeout(() => {
    this.loader = false
     this.content = true
  }, 2900);
  }

};
</script>

<style>
.loader-container{
  height: 100vh;
  background-color: black;
}
.sk-cube-grid {
  position: absolute;
  width: 40px;
  height: 40px;

}

.sk-cube-grid .sk-cube {
  width: 33%;
  height: 33%;
  background-color: #333;
  float: left;
  -webkit-animation: sk-cubeGridScaleDelay 1.3s infinite ease-in-out;
          animation: sk-cubeGridScaleDelay 1.3s infinite ease-in-out; 
}
.sk-cube-grid .sk-cube1 {
  -webkit-animation-delay: 0.2s;
          animation-delay: 0.2s; }
.sk-cube-grid .sk-cube2 {
  -webkit-animation-delay: 0.3s;
          animation-delay: 0.3s; }
.sk-cube-grid .sk-cube3 {
  -webkit-animation-delay: 0.4s;
          animation-delay: 0.4s; }
.sk-cube-grid .sk-cube4 {
  -webkit-animation-delay: 0.1s;
          animation-delay: 0.1s; }
.sk-cube-grid .sk-cube5 {
  -webkit-animation-delay: 0.2s;
          animation-delay: 0.2s; }
.sk-cube-grid .sk-cube6 {
  -webkit-animation-delay: 0.3s;
          animation-delay: 0.3s; }
.sk-cube-grid .sk-cube7 {
  -webkit-animation-delay: 0s;
          animation-delay: 0s; }
.sk-cube-grid .sk-cube8 {
  -webkit-animation-delay: 0.1s;
          animation-delay: 0.1s; }
.sk-cube-grid .sk-cube9 {
  -webkit-animation-delay: 0.2s;
          animation-delay: 0.2s; }

@-webkit-keyframes sk-cubeGridScaleDelay {
  0%, 70%, 100% {
    -webkit-transform: scale3D(1, 1, 1);
            transform: scale3D(1, 1, 1);
  } 35% {
    -webkit-transform: scale3D(0, 0, 1);
            transform: scale3D(0, 0, 1); 
  }
}

@keyframes sk-cubeGridScaleDelay {
  0%, 70%, 100% {
    -webkit-transform: scale3D(1, 1, 1);
            transform: scale3D(1, 1, 1);
  } 35% {
    -webkit-transform: scale3D(0, 0, 1);
            transform: scale3D(0, 0, 1);
  } 
}



* {
  margin: 0;
  padding: 0;
}
body {
  font-size: 16px;
  box-sizing: border-box;
  color: white;
  font-weight: 100;
}
a {
  color: white;
  text-decoration: none;
}
a:hover {
  color: rgb(223, 223, 223);
}

.bg-left {
  background-color: #bd0f4d;
  width: 50%;
  height: 1000px;
  position: absolute;
  z-index: -1;
}
.bg-right {
  background-color: #cb2964;
  width: 50%;
  height: 1000px;
  position: absolute;
  left: 50%;
  z-index: -1;
}
.heading {
  padding-top: 70px;
  font-weight: 100;
  margin-left: 70px;
  letter-spacing: 1rem;
}
.image1{
  margin-top:50px;
}
.navbar {
  position: absolute;
  transform: translateX(31%);
  margin-top: 20px;
}
.nav-link {
  margin-right: 50px;
  color: white;
  font-size: 20px;
  font-weight: 300;
  letter-spacing: 0.5rem;
}
.nav-link:hover {
  color: rgb(223, 223, 223);
}
.socials {
  position: fixed;
  top: 40%;
  right: 15px;
}
.fa {
  font-size: 35px;
  margin-bottom: 10px;
  cursor: pointer;
  transform: scale(1);
  transition: 0.3s all ease;
}
.fa:hover{
  transform: scale(1.4);
}

@media (max-width: 1199.98px) {
  .navbar {
    position: absolute;
    transform: translateX(12.5%);
  }

  .bg-right {
    width: 50.7%;
  }
}

@media (max-width: 991.98px) {
  #app{
    overflow: hidden;
  }
  .image1 {
    margin-top:0px;
    transform: scale(0.8);
  }
  .socials {
    position: static;
    margin-top: -25px;
  }
  .fa{
    margin: 0 20px;
  }
  .navbar {
    position: absolute;
    transform: translateX(19.7%);
  }
  .nav-link {
    margin-right: 7px;
    letter-spacing: 0.2rem;
  }
}

@media (max-width: 767.98px) {
 
  .navbar-toggler, .navbar-toggler:focus{
    box-shadow: none;
  }
  .navbar-nav{
    background-color: white;
    width: 90vw;
    padding-left: 20px;
  }
  .nav-link{
   
    font-size: 16px;
    font-weight: 400;
    text-align: left;
    color: black;
  }
  .bg-right, .bg-left{
    height: 100%;
  }
  .heading{
    margin-left: 0px;
  }
  .image1 {
    margin-top: 40px;
    margin-bottom: 40px;
    height: 300px;
    width: 250px;
    transform: scale(1);

  }
  .socials{
    margin-top:0px;
  }

  .navbar {
    position: absolute;
    top: 0px;
    left: 0px;
    transform: translateX(0%);
  }
  .nav-link {
    margin-right: 7px;
    letter-spacing: 0.2rem;
  }
}
@media (max-width: 575.98px) {
}
</style>
