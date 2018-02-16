<template>
    <div class="main-view" :style="renderStyle({'background':'backgroundColor'})">
      <div class="menu-frame" :style="renderStyle({'border-color':'borderColor'})">
      <span v-html="importFont()"></span>
  <!-- HEADER -->
      <div class="heading" style="display:none;">
        <div :style="renderStyle(
          {'font-size':'eventTitleSize'},
          {'font-family':'titleFont'},
          {'color':'titleColor'}
          )">
          <h3>{{account.public.events[21208].eventTitle}}</h3>
            
          <h4 style="opacity:0.5;"><i>{{account.public.events[21208].eventSubTitle}}</i></h4>
        </div>
      </div>
  <!-- ITEM1 -->
      <div class="items">
        <div class="item">
          <img :src="account.public.events[21208].items[1].photo">
          <div>
            <input 
              id="title1"
              disabled
              class="item-title toggle-disable" 
              type="text"
              spellcheck="false"
              :style="renderStyle(
              {'font-size':'titleSize'},
              {'font-family':'titleFont'},
              {'color':'titleColor'})" 
              v-model="account.public.events[21208].items[1].title"
              v-on="title = account.public.events[21208].title"
              value="title"
            >
          </div>
          <div class="item-description">
            <textarea 
              id="description1"
              disabled
              class="item-title" 
              type="text"
              spellcheck="false"
              :style="renderStyle(
              {'font-size':'descriptionSize'},
              {'font-family':'descriptionFont'},
              {'color':'descriptionColor'})"
              v-model="account.public.events[21208].items[1].description"
              v-on="description = account.public.events[21208].description"
              value="description"
            ></textarea>
          </div>
        </div>
  <!-- ITEM2 -->
        <div class="item">
          <img :src="account.public.events[21208].items[2].photo">
          <div>
            <input 
              id="title2"
              disabled
              class="item-title toggle-disable" 
              type="text"
              spellcheck="false"
              :style="renderStyle(
              {'font-size':'titleSize'},
              {'font-family':'titleFont'},
              {'color':'titleColor'})" 
              v-model="account.public.events[21208].items[2].title"
              v-on="title = account.public.events[21208].title"
              value="title"
            >
          </div>
          <div class="item-description">
            <textarea 
              id="description2"
              disabled
              class="item-title" 
              type="text"
              spellcheck="false"
              :style="renderStyle(
              {'font-size':'descriptionSize'},
              {'font-family':'descriptionFont'},
              {'color':'descriptionColor'})"
              v-model="account.public.events[21208].items[2].description"
              v-on="description = account.public.events[21208].description"
              value="description"
            ></textarea>
          </div>
        </div>
  <!-- ITEM3 -->
        <div class="item">
          <img :src="account.public.events[21208].items[3].photo">
          <div>
            <input 
              id="title3"
              disabled
              class="item-title toggle-disable" 
              type="text"
              spellcheck="false"
              :style="renderStyle(
              {'font-size':'titleSize'},
              {'font-family':'titleFont'},
              {'color':'titleColor'})" 
              v-model="account.public.events[21208].items[3].title"
              v-on="title = account.public.events[21208].title"
              value="title"
            >
          </div>
          <div class="item-description">
            <textarea 
              id="description3"
              disabled
              class="item-title" 
              type="text"
              spellcheck="false"
              :style="renderStyle(
              {'font-size':'descriptionSize'},
              {'font-family':'descriptionFont'},
              {'color':'descriptionColor'})"
              v-model="account.public.events[21208].items[3].description"
              v-on="description = account.public.events[21208].description"
              value="description"
            ></textarea>
          </div>
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
              glass3,
              borderColor,
              edit
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
    <span class="bottom-text" :style="renderStyle({'border-color':'borderColor'},{'background':'borderColor'})">{{account.public.events[21208].eventTitle}}</span>
  </div>
</template>

<style lang="scss">
.item-description{
  textarea, textarea:disabled{
    background:none !important;
    width:500px !important;
    border:none;
    text-align: center;
    resize: none ;
  }
}
    input:disabled, textarea:disabled{
      -webkit-text-fill-color:inherit;
      opacity: 1;
    }
  .bottom-text{
    background:rgb(48, 105, 230);
    border:solid rgb(48, 105, 230) 10px;
    width: 600px;
    color:white;
    font-size: 3rem;
    padding:10px 0px;
    font-family: Yellowtail;
    border-bottom-left-radius:10px;
    border-bottom-right-radius:10px;
  }
  .menu-frame{
    width:600px;
    height: 800px;
    border:solid rgb(48, 105, 230) 10px;
    border-bottom:none;
    border-top-left-radius: 10px;
    border-top-right-radius: 10px;
  }
  .main-view{
    display:flex;
    // justify-content: center;
    align-items: center;
    height: 100vh;
    flex-direction: column;
    padding-top: 40px;
  }
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
      input{
        text-align: center;
        width: 400px;
      }
      padding: 1rem 2rem;
      .item-description{
        font-size:20px;
      }
      .item-title{
        padding: 10px;
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
    background:none;
    border: none;
    color:black;
    text-align: left;
  }
// IPHONE
  @media screen and (min-device-width : 375px) 
  and (max-device-width : 667px)  {
    .menu-frame{
      width:90%;
      height: 70%;
    }
    .bottom-text{
      width:90%;
      height: auto;
      padding:0px 0px;
      font-size: 1.5rem;
    }
      .items{
        .item{
          padding:10px 0px;
          input{
            margin:auto;
            width:300px;
          }
        img{
          width:40px;
        }
        .item-title{
          font-size:20px !important;
        }
        .item-description{
          textarea{
            font-size:12px !important;
            width:300px !important;

          }
          // transform:scale(0.6);
        }
      }
    }
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
      passport: true,
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
      let url = `https://www.googleapis.com/webfonts/v1/webfonts?sort=popularity&fields=items%2Ffamily&key=AIzaSyBfo5yIc3yb6GoSY6U0jQvXhb0ryLeGfEU`
      fetch(url)
        .then((resp) => resp.json())
        .then(function (data) {
          let size = 5
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
      if (type === 'edit') {
        if (this.edit) {
          document.getElementById('title1').disabled = true
          document.getElementById('description1').disabled = true
          document.getElementById('title2').disabled = true
          document.getElementById('description2').disabled = true
          document.getElementById('title3').disabled = true
          document.getElementById('description3').disabled = true
        } else {
          document.getElementById('title1').disabled = false
          document.getElementById('description1').disabled = false
          document.getElementById('title2').disabled = false
          document.getElementById('description2').disabled = false
          document.getElementById('title3').disabled = false
          document.getElementById('description3').disabled = false
        }
      }
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