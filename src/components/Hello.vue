<template>
  <div class="hello">
    <div class="title" :class="{hide_smooth: viewSection, blur: showMenu}" @click="hideMenu">
      <vue-typer text='Hi, my name is Hanna.' :repeat='0' caret-animation='blink' :type-delay='90'></vue-typer>
      <vue-typer class="jobs" text='Full stack developer / Front end developer / Web designer' :repeat='0' caret-animation='blink' :type-delay='70' :pre-type-delay='2300'></vue-typer>

    </div>
    <div v-if="currentPage !== 'home'" class="section_title">
      {{ currentPage }}
    </div>
    <div class="menu_container" :class="{show_section: viewSection, collapsed: (!viewSection && showMenu), contact: (showMenu && (currentPage === 'contact'))} ">

      <div class="contact_container" :class="{ hide: !(currentPage === 'contact') }">
        <a class="contact_button" href="mailto: abc@example.com">Let's chat!</a>
      </div>

      <div class="about_container" :class="{ hide: !(currentPage === 'about') }">

        <div class="about_image">
          <div class="about_text">
              Lorem ipsum dolor sit amet.
          </div>
          <div class="layer"></div>
          <img src="../assets/test.jpg" alt="">
        </div>
        <div class="about_image">
          <div class="layer"></div>
          <img src="../assets/test2.jpg" alt="">
        </div>
      </div>

      <div class="back" :class="{turn: back, hide: !viewSection }" @click="goBack">
        <svg version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 32.635 32.635" style="enable-background:new 0 0 32.635 32.635;" xml:space="preserve">
          <g>
            <path d="M32.135,16.817H0.5c-0.276,0-0.5-0.224-0.5-0.5s0.224-0.5,0.5-0.5h31.635c0.276,0,0.5,0.224,0.5,0.5   S32.411,16.817,32.135,16.817z" />
            <path
              d="M13.037,29.353c-0.128,0-0.256-0.049-0.354-0.146L0.146,16.669C0.053,16.575,0,16.448,0,16.315s0.053-0.26,0.146-0.354   L12.684,3.429c0.195-0.195,0.512-0.195,0.707,0s0.195,0.512,0,0.707L1.207,16.315l12.184,12.184c0.195,0.195,0.195,0.512,0,0.707   C13.293,29.304,13.165,29.353,13.037,29.353z"/>
          </g>
          <g>
          </g>
          <g>
          </g>
          <g>
          </g>
          <g>
          </g>
          <g>
          </g>
          <g>
          </g>
          <g>
          </g>
          <g>
          </g>
          <g>
          </g>
          <g>
          </g>
          <g>
          </g>
          <g>
          </g>
          <g>
          </g>
          <g>
          </g>
          <g>
          </g>
        </svg>
      </div>

      <ul class="menu" @click="showMenu = !showMenu" :class="{show_menu : showMenu, hide : viewSection}">
        <li></li>
        <li></li>
        <li></li>
      </ul>

      <ul class="links" :class="{show_links : showMenu, hide : viewSection} ">
        <li @click="selectView('about')"><a href="#">About</a></li>
        <li @click="selectView('work')"><a href="#">Work</a></li>
        <li @click="selectView('contact')"><a href="#">Contact</a></li>
      </ul>
    </div>

  </div>
</template>

<script>
import {
  VueTyper
} from 'vue-typer'

export default {
  name: 'Hello',
  components: {
    VueTyper
  },

  data() {
    return {
      showMenu: false, // Toggle menu
      viewSection: false, // Toggle section
      back: false, // Back arrow animation
      contactForm: false, // Contact section
      currentPage: 'home'
    }
  },
  methods: {

    goBack() {
      this.back = !this.back

      // Wait for the arrow animation
      setTimeout(() => {
        // Turn arrow to initial state and collapse section
        this.back = !this.back
        this.viewSection = !this.viewSection
        this.currentPage = 'home'
      }, 600)
    },
    selectView(section) {
      this.viewSection = !this.viewSection
      this.currentPage = section
    },
    hideMenu() {
      if (this.showMenu) {
        this.showMenu = false
      }
    }
  },
  filters: {
    capitalize(value) {
      if (!value) return ''
      value = value.toString()
      return value.charAt(0).toUpperCase() + value.slice(1)
    }
  }
}
</script>

<style scoped lang="scss">

$black: #1c1b1b;
$pink: #ffb2a8;
@import url('https://fonts.googleapis.com/css?family=Montserrat:900');
.hello {
  width: 100%;
  margin: 0;
  display: flex;
  justify-content: space-between;
  height: 100%;
  color: $black!important;
  filter: blur(0);


  .section_title {
    -webkit-transform: rotate(90deg);
    transform: rotate(90deg);
    transform-origin: left;
    // top: 240px;
    position: absolute;
    left: 90px;
    top: 17px;
    font-size: 65px;
    letter-spacing: 55px;
    transition: transform 0.9s;
    color: #1c1b1b9e !important;
  }

  .title {
    width: 80%;
    margin-left: 30px;
    font-family: 'Helvetica Neue', sans-serif;
    font-size: 65px;
    font-weight: bold;
    letter-spacing: -1px;
    line-height: 1;
    text-align: left;
    margin: 135px 60px;
    opacity: 1;
    height: auto;
    transition: width 1s, opacity 1s;
    display: flex;
    flex-direction: column;

    .jobs {
      font-size: 40px;
      font-weight: initial;
      margin-top: 15px;
      margin-left: 20px;
    }

    &.hide_smooth {
      color: $black;
      width: 20px;
      margin: 0;
      transition: opacity 1s ease-out;
      opacity: 0.01;
      height: 50px;
      overflow: hidden;
      transition: width 1s, margin 0.9s;
    }
  }

  .menu_container {
    display: flex;
    align-items: center;
    justify-content: center;
    background: $black;
    transition: width 1s, margin-left 1s ease-out;

    &.collapsed {
      width: 600px;
      transition: width .9s;
    }

    &.contact {
      width: 800px!important;
      transition: width 0.6s;
    }

    &.show_section {
      width: 1250px;
      margin-left: 50px;
      transition: width 0.7s ,margin-left 0.8s ease-out;
      position: relative;
    }

    .contact_container {
      width: 100%;

height: 100%;

display: flex;

justify-content: center;

align-items: center;
      .contact_button {
        font-size: 40px;
        color: #f9c0b9;
        border: 1px solid;
        padding: 20px;
        transition: background 0.5s;
        cursor: pointer;
        text-decoration: none;
        position: absolute;

        &:hover {
          background: $pink;
          color: $black;
          transition: background 0.7s;
        }
      }
    }

    .about_container {
      width: 100%;
      height: 100%;
      display: flex;
      flex-direction: column;
      justify-content: flex-start;
      align-items: center;
      overflow: auto;

      .about_image {
        width: 500px;
        height: auto;
        margin-top: 115px;
        position: relative;
        display: flex;
        justify-content: center;
        align-items: center;

        .layer {
          height: 100%;
          width: 100%;
          position: absolute;
          background: #f9c0b9;
          opacity: 0.26;
        }

        .about_text {
          position: absolute;
          min-width: 775px;
          color: $pink;
          mix-blend-mode: difference;
          font-size: 45px;
          top: 120px;
          right: 10px;
          z-index: 10;
        }

        img {
          width: 100%;
          height: auto;
        }
      }
    }

    .back {
      position: absolute;
      top: 0;
      left: 0;
      margin: 40px;
      color: white;
      width: 45px;
      cursor: pointer;

      &.turn {
        transform: rotate(-90deg);
        transition: transform 0.5s;
      }

      svg {
        fill: $pink;
      }
    }

    ul.menu {
      height: auto;
      width: 75px;
      padding: 0 30px;
      transition: width 0.6s;
      cursor: pointer;

      li {
        position: relative;
        background: $pink;
        margin: 3px;
        height: 4px;
        width: 70px;
        transition: transform 0.3s, width 0.3s; //burger menu grow
        display: inline-block;
      }
    }

    .show_menu {
      cursor: pointer;
      margin: 10px!important !important;
      transition: width 0.9s;
      transition: margin 0.9s;

      li {
        background: $pink;

        &:nth-child(1) {
          top: 25px;
          transform: rotate(135deg);
          transition: transform 0.3s;
        }

        &:nth-child(2) {
          width: 0;
          transition: width 0.3s;
        }

        &:nth-child(3) {
          bottom: 19px;
          transform: rotate(-135deg);
          transition: transform 0.3s;
        }
      }
    }

    ul.links {
      overflow: hidden;
      width: 0;
      margin-left: 0;
      transition: width .8s, margin-left .8s;
      text-align: left;
      padding: 0;

      &.show_links {
        width: 370px !important;
        margin-left: 35px !important;
        transition: width .8s, margin-left .8s;
      }

      li {
        margin: 20px 5px;

        a {
          color: $pink;
          text-decoration: none;
          transition: color 0.5s;
          font-family: 'Helvetica Neue', sans-serif;
          font-size: 60px;
          font-weight: 600;
          letter-spacing: -1px;
          line-height: 1.4;
          transition: margin-left 0.5s;

          &:hover {
            margin-left: 20px;
            transition: color 0.7s, margin-left 0.5s;
          }
        }
      }
    }
  }

  .blur {
    filter: blur(5px);
  }

  .hide {
    display: none!important;
  }
}

</style>
