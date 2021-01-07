<template>
  <div id="app">
    <h1>{{data.name}}</h1>
    <div class="image-container"><img src="./images/woman-in-pink.jpg" alt="woman in pink"></div>
    <div class="nav-container">
      <a href="">HOME</a>
      <a href="">ABOUT</a>
      <div class="portrait-image-container"><img src="./images/portrait-woman.jpg" alt="portrait"></div>
      <a href="">GALLERY</a>
      <a href="">CONTACT</a>
    </div>
    <div class="icon-container">
      <a class="icon" :href="`https://instagram.com/${data.social_media.instagram}?igshid=pujrhcnbzzi3`" target="_blank" rel="noopener"><img src="./images/instagram-line.png" alt="instagram"></a>
      <a class="icon" :href="`https://twitter.com/${data.social_media.twitter}`" target="_blank" rel="noopener"><img src="./images/twitter-line.png" alt="twitter"></a>
      <a class="icon" :href="`https://www.snapchat.com/add/${data.social_media.snapchat}`" target="_blank" rel="noopener"><img src="./images/snapchat-line.png" alt="snapchat"></a>
      <a class="icon" :href="`mailto:${data.social_media.email}`"><img src="./images/mail-line.png" alt="email"></a>
    </div>
  </div>
</template>

<script>

export default {
  name: "App",
  data() {
    return {
      data: {}
    }
  },
  beforeMount(){
    this.getData();
  },
  methods: {
    async getData(){
      const res = await fetch('https://hirng-x2021.glitch.me/api');
      const data = await res.json();
      this.data = data;
    }
  }
}
</script>

<style>
body {
  padding: 0;
  margin: 0;
  background: linear-gradient(to right, #c71847 50%, #d93b65 50%);
}

h1 {
  font-weight: 100;
  text-align: center;
  color: white;
  letter-spacing: 0.5em;
  margin: 2em 0;
}

.nav-container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 60%;
  margin: 3em auto;
}

.nav-container>a {
  text-decoration: none;
  color: white;
  width: 5em;
  letter-spacing: 0.3em;
}

.portrait-image-container {
  width: 5em;
  height: auto;
}

.portrait-image-container>img {
  max-width: 100%;
  border-radius: 50%;
  border: 1px solid white;
}

.icon-container {
  display: flex;
  flex-wrap: wrap;
  align-content: space-around;
  height: 20%;
  width: 2em;
  position: absolute;
  top: 40%;
  right: 1em;
}

.icon {
  display: block;
}

.image-container {
  width: 25em;
  height: 25em;
  margin: 0 auto;
  box-shadow: 0.3em 0.3em 1em 0.3em rgba(0,0,0,0.3);
}

.image-container>img {
  max-width: 100%;
}
</style>
