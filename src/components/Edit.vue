<template>
    <div class="admin">
      {{isLogged()}}
      {{banner}}
      <div class="edit-control">
        <img v-show="isLoggedIn" title="logout" alt="logout" src="../assets/icons/power-off.svg" class="icon" v-on:click="signOut(), toggle('login_closed')">
        <img v-on:click="toggle('edit')" title="close-edit" alt="close-edit" class="icon" src="../assets/icons/close-out.svg">
      </div>
      <div class="info-panel" v-show="isLoggedIn">
      <!-- INFO -->
        <div class="panel">
          <span class="categories" v-on:click="toggle('passport')">
            <img alt="close" class="icon" src="../assets/icons/id.svg">
            <div v-if="passport">
              <img alt="close" class="icon arrow" src="../assets/icons/arrow-right.svg">
            </div>
            <div v-else>
              <img alt="close" class="icon arrow" src="../assets/icons/arrow-left.svg">
            </div>
          </span>
          <!-- <transition name="fade"> -->
            <div class="panel-contents" v-if="passport">
              <div>
                <div>Event Title</div>
                <input 
                  id="Event_Title" 
                  v-model="account.public.events[21208].eventTitle" 
                  v-on="childName = account.public.events[21208].eventTitle" 
                  placeholder="Name"
                >
              </div>
              <div>
                <div>Event SubTitle</div>
                <input 
                  id="Event_SubTitle" 
                  v-model="account.public.events[21208].eventSubTitle" 
                  v-on="childName = account.public.events[21208].eventSubTitle" 
                  placeholder="Name"
                >
              </div>
                <p></p>
              <div>
                <div>First Title</div>
                <input 
                  id="1_Title" 
                  v-model="account.public.events[21208].items[1].title" 
                  v-on="childName = account.public.events[21208].items[1].title" 
                  placeholder="Name"
                >
              </div>
              <div>
                <div>First Description</div>
                <input 
                  id="1_Description" 
                  v-model="account.public.events[21208].items[1].description" 
                  v-on="childName_description = account.public.events[21208].items[1].description" 
                  placeholder="Description"
                >
              </div>
              <div>
                <div>Glasswear</div>
                <div class="glass-choose">
                  <img v-on:click="pickGlass('1', 'cocktail')" :src="account.images.cocktail">
                  <img v-on:click="pickGlass('1', 'rocks')" :src="account.images.rocks">
                  <img v-on:click="pickGlass('1', 'collins')"  :src="account.images.collins">
                </div>
              </div>

                <p></p>

              <div>
                <div>Second Title</div>
                <input 
                  id="2_Title" 
                  v-model="account.public.events[21208].items[2].title" 
                  v-on="childName = account.public.events[21208].items[2].title" 
                  placeholder="Name"
                >
              </div>
              <div>
                <div>Second Description</div>
                <input 
                  id="2_Description" 
                  v-model="account.public.events[21208].items[2].description" 
                  v-on="childName_description = account.public.events[21208].items[2].description" 
                  placeholder="Description"
                >
              </div>
              <div>
                <div>Glasswear</div>
                <div class="glass-choose">
                  <img v-on:click="pickGlass('2', 'cocktail')" :src="account.images.cocktail">
                  <img v-on:click="pickGlass('2', 'rocks')" :src="account.images.rocks">
                  <img v-on:click="pickGlass('2', 'collins')"  :src="account.images.collins">
                </div>
              </div>

                <p></p>

              <div>
                <div>Third Title</div>
                <input 
                  id="3_Title" 
                  v-model="account.public.events[21208].items[3].title" 
                  v-on="childName = account.public.events[21208].items[3].title" 
                  placeholder="Name"
                >
              </div>
              <div>
                <div>Third Description</div>
                <input 
                  id="3_Description" 
                  v-model="account.public.events[21208].items[3].description" 
                  v-on="childName_description = account.public.events[21208].items[3].description" 
                  placeholder="Description"
                >
              </div>
              <div>
                <div>Glasswear</div>
                <div class="glass-choose">
                  <img v-on:click="pickGlass('3', 'cocktail')" :src="account.images.cocktail">
                  <img v-on:click="pickGlass('3', 'rocks')" :src="account.images.rocks">
                  <img v-on:click="pickGlass('3', 'collins')"  :src="account.images.collins">
                </div>
              </div>  
          </div>
      </div>

    <!-- SOCIALS -->
    <!-- <div class="panel">
        <span class="categories" v-on:click="toggle('social')">
          <img alt="close" class="icon" src="../assets/icons/social.svg">
          <div v-if="social">
            <img alt="close" class="icon arrow" src="../assets/icons/arrow-right.svg">
          </div>
          <div v-else>
            <img alt="close" class="icon arrow" src="../assets/icons/arrow-left.svg">
          </div>
        </span>
      <transition name="fade">
        <div class="panel-contents" v-if="social">
          <div>
            <div>Instagram</div>
            <input 
              id="instagram" 
              v-model="fbInfo.instagram" 
              v-on="instagram = fbInfo.instagram" 
              placeholder="instagram"
            >
          </div>
          <div>
            <div>Twitter</div>
            <input 
              id="twitter" 
              v-model="fbInfo.twitter" 
              v-on="twitter = fbInfo.twitter" 
              placeholder="twitter"
            >
          </div>
          <div>
            <div>Facebook</div>
            <input 
              id="facebook" 
              v-model="fbInfo.facebook" 
              v-on="facebook = fbInfo.facebook" 
              placeholder="facebook"
            >
          </div>
          <div>
            <div>Message Email</div>
            <input 
              id="messageEmail" 
              v-model="fbInfo.messageEmail" 
              v-on="messageEmail = fbInfo.messageEmail" 
              placeholder="messageEmail"
            >
          </div>
        </div>
      </transition>
    </div> -->
  <!-- IMAGE -->
    <!-- <div class="panel">
      <span class="categories" v-on:click="toggle('image')">
        <img alt="close" class="icon" src="../assets/icons/camera.svg">
        <div v-if="image">
          <img alt="close" class="icon arrow" src="../assets/icons/arrow-right.svg">
        </div>
        <div v-else>
          <img alt="close" class="icon arrow" src="../assets/icons/arrow-left.svg">
        </div>
      </span>
      <transition name="fade">
        <imagepicker
          v-bind="{
            fbImages,
            image,
            images
          }"
        />
      </transition>
    </div> -->
  <!-- COLORS -->
    <div class="panel">
      <span class="categories" v-on:click="toggle('color')">
        <img alt="close" class="icon" src="../assets/icons/paint-white.svg">
        <div v-if="color">
          <img alt="close" class="icon arrow" src="../assets/icons/arrow-right.svg">
        </div>
        <div v-else>
          <img alt="close" class="icon arrow" src="../assets/icons/arrow-left.svg">
        </div>
      </span>
      <transition name="fade">
        <div class="panel-contents" v-if="color">
          <div class="panel-category">
            <span>Title Color</span>
            <colorpicker 
              class="stylepicker"
              colorInstance="titleColor"
              v-bind="{
                colorWindow,
                toggle,
                fbInfo,
                titleColor,
                account
              }"
            />
            <input 
              id="title-color" 
              v-model="account.public.events[21208].titleColor" 
              v-on="titleColor = account.public.events[21208].titleColor"
              value="titleColor"
            >
          </div>

          <div class="panel-category">
            <span>Description Color</span>
            <colorpicker 
              class="stylepicker"
              colorInstance="descriptionColor"
              v-bind="{
                colorWindow,
                toggle,
                fbInfo,
                account,
                descriptionColor
              }"
            />
            <input 
              id="description-color" 
              v-model="account.public.events[21208].descriptionColor" 
              v-on="headerSubColor = account.public.events[21208].descriptionColor" 
              placeholder=""
            >
          </div>
        <!-- FONTS -->
          <div class="panel-category">
            <span class="category-close">
              Font Face
            </span>
            <fontpicker 
              class="stylepicker"
              fontInstance="titleFont"
              v-bind="{
                colorWindow,
                toggle,
                fbInfo,
                fontImport,
                importFont,
                fonts,
                fontSort,
                account,
                titleFont
              }"
            />
            <input 
              style="visibility:hidden;"
              id="font-style" 
              v-model="account.public.events[21208].titleFont" 
              v-on="fontStyle = account.public.events[21208].titleFont" 
              placeholder=""
            >
          </div>

        </div>
      </transition>
    </div>
    <transition name="slide-fade">
      <h4>{{this.displayNote}}</h4>
    </transition>
    <!-- SUBMIT BUTTON -->
    <div class="edit-control submit">
      <img
        alt="Submit Changes"
        title="Submit Changes" 
        class="icon arrow" 
        src="../assets/icons/check.svg"
        href="/"
        v-on:click="
        changeProp(
          'title1', 
          'title1_description', 
          'name', 
          'name_description',
          'instagram',
          'twitter',
          'facebook',
          'messageEmail',
          'contact',
          'contact_description',
          'banner',
          'location',
          'fontColor',
          'fontStyle',
          'fontImport',
          'images',
          'account',
          'descriptionFont',
          'descriptionSize',
          'titleFont',
          'titleSize',
          'titleColor',
          'descriptionColor',
          'glass1',
          'glass2',
          'glass3'
        )"
      >
      <img
        class="icon"
        title="Cancel Changes" 
        alt="Cancel Changes" 
        src="../assets/icons/exit-red.svg"
      >
    </div>
  </div> 

    <!-- LOGIN -->
      <div class="account" v-bind:class="login_closed ? 'closed' : ''">
        <login 
          v-bind="{
            isLoggedIn,
            toggle,
            isLogged,
            banner
          }"
        />
      </div>
    </div>
    
</template>
<script>
    import firebase from 'firebase'

    export default {
      name: 'edit',
      props: [
        'toggle',
        'fbInfo',
        'isLogged',
        'isLoggedIn',
        'changeProp',
        'contact',
        'contact_description',
        'id',
        'social',
        'passport',
        'image',
        'color',
        'fontImport',
        'importFont',
        'fonts',
        'displayNote',
        'fontSort',
        'images',
        'account',
        'descriptionFont',
        'descriptionSize',
        'titleFont',
        'titleSize',
        'titleColor',
        'descriptionColor',
        'glass1',
        'glass2',
        'glass3'
      ],
      data: function () {
        return {
          childName: this.name,
          childName_description: this.name_description,
          banner: '',
          headerColorChild: this.headerColor,
          x: 0,
          y: 0,
          blur: 0
        }
      },
      methods: {
        pickGlass (item, glass) {
          this.account.public.events[21208].items[item].photo = this.account.images[glass]
        },
        signOut (props) {
          let self = this
          firebase.auth().signOut().then(function () {
            console.log('signedout')
            self.isLogged()
            self.email = ''
            self.password = ''
            self.childBanner = ''
          }, function (error) {
            console.log(error)
          })
        },
        mounted: function () {
        }
      }
    }
</script>

<style lang="scss">
  .glass-choose{
    display:flex;
    justify-content: space-between;
    align-items: center;
    cursor: pointer;
    img{
      filter:invert(1);
      width:30px;
      margin:2px;
      height:auto;
      // background:rgba(0,0,0,0.1);
      border-radius: 5px;
      border: solid 2px rgba(0,0,0,0.1);
    }
  }
  .category-close{
    display: flex;
    justify-content: space-between;
    align-content: center;
    img{
    opacity: 0.4;
    padding:0 5px;
    width:12px;
    }
  }
  .edit-control{
    display:flex;
    justify-content: space-between;
    align-content: center;
    padding:0.8rem 0.2rem;
  }
  .submit{
    height: 75px;
    width:100px;
    margin:auto;
    justify-content: space-around;
  }
  .px{
    font-size: 0.8rem;
    margin: auto;
    input{
      width: 15px !important;
      padding:2px;
    }
  }
  .slide-fade-enter-active {
    transition: all .3s ease;
  }
  .slide-fade-leave-active {
    transition: all .3s cubic-bezier(1.0, 0.5, 0.8, 1.0);
  }
  .slide-fade-enter, .slide-fade-leave-to
  {
    transform: translateX(10px);
    opacity: 0;
  }
  .fade-enter-active, .fade-leave-active {
    transition: opacity .1s;
  }
  .fade-enter, .fade-leave-to {
    opacity: 0;
  }
  .admin_panel{
    z-index: 100;
    position: fixed;
    right:0;
    top:0;
    .categories{
      font-weight: 800;
      cursor: pointer;
      display: block;
    }
    input{
      background:rgba(0, 0, 0, 0.25);
      color:white;
      font-weight: 600;
      font-size: 0.8rem;
      border:none;
      padding:0.3rem;
      margin:0.2rem 0px;
      border-radius: 3px;
    }
    .admin{
      span{
        color:rgba(255, 255, 255, 0.4);
      }
      height:100vh;
      overflow-y: auto;
      padding:1rem;
      min-width: 170px;
      background:#16141e;
      box-shadow: 0 0 30px black;
      .panel{
        background: rgba(255, 255, 255, 0.05);
        padding: 10px;
        border-radius: 10px;
        margin: 10px 0;
        div{
          text-align: left;
        }
        .panel-contents{
          display: flex;
          align-content: center;
          flex-direction: column;
          padding:10px 0px;
          color:rgba(255, 255, 255, 0.3);
          .panel-category{
            // border-bottom: 1px solid #ffffff2b;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            flex-wrap:wrap;
            .stylepicker{
              padding:5px 0px;
            }
            margin:10px 0px;
            span{
              margin-bottom:5px;
            }
          }
        }
        .categories{
          display: flex;
          justify-content: space-between;
          align-content: center;
        }
      }
    }
  }
  @media screen and (max-device-width: 1024px) {
      .glass-choose{
        img{
          width:20px;
        }
      }
      .admin_panel{
        margin: auto;
        input{
          width:80px;
          font-size:0.6rem;
        }
        .admin{
          width:100px;
          min-width: 100px;
          padding:5px;
          span{
            font-size: 0.7rem;
          }
          .panel{
            padding:10px 3px;
          }
        }
      }
      .panel-contents{
        div{
          div{
            font-size:10px;
          }
        }
      }
      .panel-category{
        span{
          font-size: 0.7rem;
        }
      }
    }
</style>