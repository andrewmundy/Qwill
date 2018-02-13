<template>
    <div class="main-view">
      <span v-html="importFont()"></span>
  <!-- HEADER -->
      <div class="heading">
        <div :style="renderStyle(
          {'font-size':'eventTitleSize'}
          )">
          <h1>{{account.public.events[21208].eventTitle}}</h1>
            
          <h2><i>{{account.public.events[21208].eventSubTitle}}</i></h2>
        </div>
      </div>
  <!-- ITEM1 -->
      <div class="items">
        <div class="item">
          <img :src="account.public.events[21208].items[1].photo">
          <div class="item-title" :style="renderStyle(
            {'font-size':'titleSize'},
            {'font-family':'titleFont'},
            {'color':'titleColor'})"
          >{{account.public.events[21208].items[1].title}}</div>
          <div class="item-description" :style="renderStyle(
            {'font-size':'descriptionSize'},
            {'font-family':'descriptionFont'},
            {'color':'descriptionColor'})"
          >{{account.public.events[21208].items[1].description}}</div>
        </div>
  <!-- ITEM2 -->
        <div class="item">
          <img :src="account.public.events[21208].items[2].photo">
          <div class="item-title" :style="renderStyle(
            {'font-size':'titleSize'},
            {'font-family':'titleFont'},
            {'color':'titleColor'})"
          >{{account.public.events[21208].items[2].title}}</div>
          <div class="item-description" :style="renderStyle(
            {'font-size':'descriptionSize'},
            {'font-family':'descriptionFont'},
            {'color':'descriptionColor'})"
          >{{account.public.events[21208].items[2].description}}</div>
        </div>
  <!-- ITEM3 -->
        <div class="item">
          <img :src="account.public.events[21208].items[3].photo">
          <div class="item-title" :style="renderStyle(
            {'font-size':'titleSize'},
            {'font-family':'titleFont'},
            {'color':'titleColor'})"
          >{{account.public.events[21208].items[3].title}}</div>
          <div class="item-description" :style="renderStyle(
            {'font-size':'descriptionSize'},
            {'font-family':'descriptionFont'},
            {'color':'descriptionColor'})"
          >{{account.public.events[21208].items[3].description}}</div>
        </div>
      </div>

      <img class="icon settings" src="../assets/icons/cogs.svg" v-on:click="toggle('edit')">
      <div class="admin_panel">
        <transition name="slide-fade">
          <edit 
            v-if="edit"
            v-bind="{
              fontSort,
              fbInfo,
              toggle,
              passport,
              isLogged,
              isLoggedIn,
              changeProp,
              name,
              name_description,
              contact,
              contact_description,
              title1,
              title1_rescription,
              instagram,
              twitter,
              facebook,
              info,
              messageEmail,
              fbInfo,
              social,
              image,
              banner,
              location,
              color,
              headerColor,
              headerSubColor,
              colorWindow,
              shadow,
              fontColor,
              fontStyle,
              fontImport,
              importFont,
              fonts,
              displayNote,
              fbImages,
              images,
              account,
              descriptionFont,
              descriptionSize,
              titleFont,
              titleSize,
              titleColor,
              descriptionColor,
              glass1,
              glass2,
              glass3
            }"
          />
        </transition>
      </div>



      <!-- <div class="spacer"></div>
      
      <img class="hidden hidden-right squiggle" v-fbInfocus="'showElement-slow'" src="../assets/squiggle.svg">
        <h1 class="genre-titles">
          {{fbInfo.title1}}
        </h1>
        <h2 class="genre-quote hidden hidden-left" v-fbInfocus="'showElement'">
          {{fbInfo.title1_description}}
        </h2> -->

      <!-- <projects/> -->
      <!-- <contact 
        v-bind="{
          contact, 
          contact_description, 
          changeProp, 
          fbInfo, 
          edit,
          toggle
          }" 
        /> -->
    </div>
</template>

<style lang="scss">
  .heading{
    padding:2rem;
  }
  .items{
    display:flex;
    justify-content: center;
    align-content: center;
    flex-direction: column;
    text-align: center;
    .item{
      padding:1rem 5rem;
      .item-description{
        font-size:20px;
      }
      .item-title{
        padding: 20px;
      }
    }
    img{
      width:100px;
      height: auto;
    }
  }
  button{
    background: rgba(0, 0, 0, 0.253);
    color: #ffffff4d;
    border-radius: 20px;
    border:none;
    padding:7px 10px;
    font-size: 0.8rem;
    font-weight: 600;
  }
  .closed{
    display:none;
  }
  #edit{
    text-align: left;
    padding: 0rem 1rem;
  }
  input{
    background:white;
    color:black;
    text-align: left;
  }
</style>

<script>
import Vue from 'vue'
import firebase from 'firebase'
import VueFire from 'vuefire'
import VueResource from 'vue-resource'

let config = {
  apiKey: 'AIzaSyCuvCKY3Q2LRN0-9B-ZicYEjAcvP5jFY-w',
  authDomain: 'qwill-7f640.firebaseapp.com',
  databaseURL: 'https://qwill-7f640.firebaseio.com',
  projectId: 'qwill-7f640',
  storageBucket: 'qwill-7f640.appspot.com',
  messagingSenderId: '484437909074'
}

Vue.use(VueFire)
Vue.use(VueResource)

let app = firebase.initializeApp(config)
let db = app.database()
let storage = firebase.storage()

export default {
  name: 'Main',
  data () {
    return {
      fonts: [],
      title1: '',
      title1_description: '',
      name: '',
      name_description: '',
      closed: true,
      login_closed: true,
      edit: false,
      a: 'a',
      login: 'login',
      img: '',
      isLoggedIn: false,
      imageArray: [],
      contact: '',
      contact_description: '',
      header_data: false,
      instagram: '',
      twitter: '',
      facebook: '',
      passport: false,
      fbInfo: false,
      social: false,
      image: false,
      color: false,
      banner: '',
      location: '',
      headerColor: '',
      headerSubcolor: '',
      colorWindow: false,
      shadow: '',
      fontColor: '',
      fontStyle: '',
      fontSort: '',
      fontData: '',
      displayNote: '',
      images: [],
      headerImage: '',
      glass1: '',
      glass2: '',
      glass3: ''
    }
  },
  firebase: {
    account: {
      source: db.ref('accounts'),
      asObject: true
    }
  },
  created: function () {
  },
  mounted: function () {
    this.fetchFont()
    this.isLogged()
  },
  methods: {
    createNote: function (message) {
      this.displayNote = message
      let self = this

      setTimeout(function () {
        self.displayNote = ''
        console.log('cleared')
      }, 1000)
    },
    fetchFont: function () {
      let self = this
      let url = `https://www.googleapis.com/webfonts/v1/webfonts?sort=trending&fields=items%2Ffamily&key=AIzaSyBfo5yIc3yb6GoSY6U0jQvXhb0ryLeGfEU`
      fetch(url)
        .then((resp) => resp.json())
        .then(function (data) {
          let size = 10
          let items = data.items
          items.slice(0, size).map(function (font) {
            self.fonts.push(font.family)
          })
        })
        .catch(function (err) {
          console.log(err)
        })
    },
    importFont () {
      let self = this
      let imported = self.account.public.events[21208].fontImport
      if (imported) {
        let url = `<style> @import url('//fonts.googleapis.com/css?family=${imported}')</style>`
        self.account.public.events[21208].fontStyle = self.account.public.events[21208].fontImport
        return url
      }
    },
    renderStyle (...args) {
      let style = {}
      let self = this
      args.map(function (arg) {
        let key = Object.keys(arg)[0]
        let value = Object.values(arg)[0]
        style[key] = self.account.public.events['21208'][value]
      })
      return style
    },
    isLogged () {
      let self = this
      if (!self.account.public.events[21208].requireAuth) {
        this.isLoggedIn = true
      } else if (firebase.auth().currentUser) {
        this.isLoggedIn = true
      } else {
        this.isLoggedIn = false
      }
    },
    scrollMeTo (refName) {
      let element = this.$refs[refName]
      let top = element.offsetTop
      window.scrollTo(0, top)
    },
    changeProp: function (...args) {
      let self = this
      let updates = {}
      let notes = ''
      if (!this.requireAuth) {
        args.map(function (arg) {
          updates[arg] = self.account.public.events[21208][arg]
          notes = 'cool!'
        })
        db.ref('info').update(updates)
        // console.log(updates)
      } else if (this.requireAuth) {
        if (firebase.auth().currentUser) {
          args.map(function (arg) {
            updates[arg] = self.account.public.events[21208][arg]
          })
          db.ref('fbInfo').update(updates)
          console.log(updates)
        } else {
          console.log('oops')
        }
      }
      this.createNote(notes)
    },
    imagesRef (file) {
      storage.ref('images/' + file + '.jpg').getDownloadURL().then(function (url) {
        let img = document.getElementById(file)
        img.src = url
      }).catch(function (error) {
        console.log('oops ' + error)
      })
    },
    toggle (type) {
      if (this[type]) {
        this[type] = false
      } else if (!this[type]) {
        this[type] = true
      }
    }
  },
  directives: {
    fbInfocus: {
      isLiteral: true,
      inserted: (el, binding, vnode) => {
        let f = () => {
          let rect = el.getBoundingClientRect()
          let inView = (
            rect.width > 0 &&
            rect.height > 0 &&
            rect.top >= 0 &&
            rect.bottom <= (window.innerHeight - 50 || document.documentElement.clientHeight)
          )
          if (inView) {
            el.classList.add(binding.value)
            window.removeEventListener('scroll', f)
          }
        }
        window.addEventListener('scroll', f)
        f()
      }
    }
  }
}
</script>