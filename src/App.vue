<template>
  <v-app>
    <div class="appbar-mobile d-flex align-center justify-space-between">
      <div class="ml-2 white--text brandname">ROY MAGDAONG</div>
      <v-btn icon @click="navbar = !navbar" class="mr-2">
        <v-icon  color="white" >mdi-menu</v-icon>
      </v-btn>
    </div>
    <div class="appbar-mobile-content d-flex flex-column white--text justify-space-around" :class="{'slide-down-link': navbar, 'slide-up-link': !navbar}">
      <div class="links d-flex align-center justify-center" :class="{'active-link': isIntersectingAbout}" @click="scrollTo('#about')">ABOUT</div>
      <div class="links d-flex align-center justify-center" :class="{'active-link': isIntersectingSkills}" @click="scrollTo('#skills')">SKILLS</div>
      <div class="links d-flex align-center justify-center" :class="{'active-link': isIntersectingProjects}" @click="scrollTo('#projects')">PROJECTS</div>
      <div class="links d-flex align-center justify-center" :class="{'active-link': isIntersectingEducation}" @click="scrollTo('#education')">EDUCATION</div>
      <div class="links d-flex align-center justify-center" :class="{'active-link': isIntersectingExperience}" @click="scrollTo('#experience')">EXPERIENCE</div>
    </div>

    <div style="margin-top:50px;"></div>
    <v-main class="main" :class="{'slide-down': navbar, 'slide-up': !navbar}">
      <v-container class="pa-0">
        <div id="about">
          <div class="section-title">ABOUT</div>
          <div class="intersection-element" v-intersect="onIntersectAbout"></div>
        </div>
        <div id="skills" >
          <div class="section-title">SKILLS</div>
          <div class="intersection-element" v-intersect="onIntersectSkills"></div>
        </div>
        <div id="projects" >
          <div class="section-title">PROJECTS</div>
          <div class="intersection-element" v-intersect="onIntersectProjects"></div>
        </div>
        <div id="education" >
          <div class="section-title">EDUCATION</div>
          <div class="intersection-element" v-intersect="onIntersectEducation"></div>
        </div>
        <div id="experience" >
          <div class="section-title">EXPERIENCE</div>
          <div class="intersection-element" v-intersect="onIntersectExperience"></div>
        </div>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>

export default {
  name: 'App',
  components: {
  },

  data: () => ({
    navbar: false,
    menu2: false,
    isIntersectingAbout: false,
    isIntersectingSkills: false,
    isIntersectingProjects: false,
    isIntersectingEducation: false,
    isIntersectingExperience: false,
  }),
  created(){
    
  },
  methods:{
    scrollTo(target){
      this.navbar = false;
      // const vh = document.documentElement.clientHeight || 0;
      this.$vuetify.goTo(target, {duration: 700, offset: 50, easing: 'easeInOutCubic'})
    },
    onIntersectAbout (entries, observer, isIntersecting) {
      this.isIntersectingAbout = isIntersecting
    },
    onIntersectSkills (entries, observer, isIntersecting) {
      this.isIntersectingSkills = isIntersecting
    },
    onIntersectProjects (entries, observer, isIntersecting) {
      this.isIntersectingProjects = isIntersecting
    },
    onIntersectEducation (entries, observer, isIntersecting) {
      this.isIntersectingEducation = isIntersecting
    },
    onIntersectExperience (entries, observer, isIntersecting) {
      this.isIntersectingExperience = isIntersecting
    },
  }
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Open+Sans:ital,wght@0,300;0,400;0,600;0,700;0,800;1,300;1,400;1,600;1,700;1,800&family=Source+Sans+Pro:ital,wght@0,200;0,300;0,400;0,600;0,700;0,900;1,200;1,300;1,400;1,600;1,700;1,900&display=swap');
.v-application {
  font-family: 'Open Sans', sans-serif !important;
}
.appbar-mobile{
  width: 100%;
  background-color: rgb(6, 129, 123);
  height: 50px;
  position: fixed;
  top: 0;
  z-index: 3;
}
.appbar-mobile-content{
  width: 100%;
  height: 250px;
  background-color: rgb(6, 129, 123);
  margin-top: 50px;
  position: fixed;
  top: 0;
  z-index: 2;
  letter-spacing: 4px;
  font-size: 13px;
  font-weight: 600;
}
.links{
  border-top: 1px solid rgb(29, 151, 145);
  height: 20%;
}
.links:hover{
  cursor: pointer;
  background-color: rgb(89, 236, 229);
  font-size: 15px;
}
.brandname{
  letter-spacing: 2px;
  font-size: 13px;
  font-weight: 600;
}
.main{
  transform: translate3d(0,0,0);
  background-color: white;
}
.active-link{
  background-color: rgb(89, 236, 229);
  font-size: 15px;
  color: rgb(58, 56, 56);
  font-weight: 700;
}

/* appbar animation */
.slide-up{
  transform: translate3d(0,0,0) !important;
  transition: transform 0.4s !important;
}
.slide-down{
  transform: translate3d(0,250px,0) !important;
  transition: transform 0.7s !important;
}
.slide-up-link{
  transform: translate3d(0,-250px,0);
  transition: transform 0.4s;
}
.slide-down-link{
  transform: translate3d(0,0,0);
  transition: transform 0.7s;
}

/* sections */
.section-title{
  text-align: center;
  font-size: 14px;
  font-weight: 700;
  letter-spacing: 1px;
  margin-top: 4px;
  color: rgb(58, 56, 56);
}
#about{
  position: relative;
  min-height: 100vh;
  background-color: white;
}
#skills{
  position: relative;
  min-height: 100vh;
  background-color: rgb(218, 214, 214);
}
#projects{
  position: relative;
  min-height: 100vh;
  background-color: white;
}
#education{
  position: relative;
  min-height: 100vh;
  background-color: rgb(218, 214, 214);
}
#experience{
  position: relative;
  min-height: 100vh;
  background-color: white;
}

.intersection-element{
  position: absolute;
  bottom: 75%;
  width: 100%;
}
</style>
