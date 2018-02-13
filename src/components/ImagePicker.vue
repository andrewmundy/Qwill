<template>
    <div>
      <div class="image-import" v-if="image">
        <div v-if="imageUrl" class="image-import">
          <input v-model="imageTitle" value="name">
          <input v-model="imageDescription" value="description">

          <img :src="imageUrl">
          <button @click="onCreateImage()"> Upload </button>
          <button @click="cancelCreateImage()"> Cancel </button>
        </div>
        <div v-else>
          <button @click="onPick()"> Upload </button>
        </div>
        <input 
          @change="onFilePicked"
          type=file 
          style="display:none;" 
          ref="fileInput" 
          accept="image/*"
        > 
      <div class="display-photos">
        <div id="photos">
          <div class="photo" v-for="thumb in thumbnails">
            <img :src="thumb.imageUrl">
            <span class="photo-title">{{thumb.title}}</span>
            <span class="photo-description">{{thumb.description}}</span>
          </div>
        </div>
      </div>
      </div>
    </div>
</template>

<style lang="scss">
    #photos{
      display:flex;
      justify-content: flex-start;
      flex-direction: row;
      flex-wrap: wrap;
      width:auto;
      .photo{
        flex-direction: column;
        flex-wrap:wrap;
        margin:auto;
        // background:white;
        .photo-title, .photo-description{
        font-size: 0.3rem;
        color:black;
        }
        img{
          width:50px;
          margin:5px;
        }
      }
    }
    .image-import{
      display: flex;
      justify-content: center;
      flex-direction: column;
      width:auto;
      padding:10px 0px;
      width:150px;
      img{
        margin:auto;
        width:100px;
      }
      button{
        background:rgba(255,255,255,0.2);
        border-radius: 4px;
        padding:4px;
        cursor: pointer;
      }
      *{
        margin:5px 0px;
      }
      a{
        text-decoration: underline;
      }
      i{
        font-size:0.6rem;
      }
    }
    .font-window{
      display: flex;
      justify-content: flex-start;
      align-content: center;
      flex-wrap: wrap;
      // flex-direction: column;
      width:150px;
      margin: 10px 0px;
      li{
        background:rgba(255,255,255,0.2)
      }
      *{
        // background:rgba(255,255,255,0.2);
        border-radius: 4px;
        padding:4px;
        margin: 2px;
        cursor: pointer;
      }
    }
    @media screen and (max-device-width: 1024px) {
      .stylepicker{
        width:100px;
        font-size: 0.6rem;
        .font-window{
          width:auto;
          // padding:5px;
          *{
            border-radius: 5px;
            margin: 6px 0px 6px 0px;
          }
        }
        .image-import{
          padding:5px;
        }
      }
    }
</style>

<script>
  import firebase from 'firebase'
  export default {
    name: 'FontPicker',
    props: [
      'fbImages',
      'image',
      'images'
    ],
    data () {
      return {
        imageTitle: 'Title',
        imageUrl: '',
        imageDescription: 'Description',
        title: '',
        imageSelect: '',
        thumbnails: []
      }
    },
    methods: {
      imageGet () {
        let self = this
        let imagesRef = firebase.database().ref('images')
        imagesRef.on('value', function (snapshot) {
          let images = snapshot.val()
          for (let image in images) {
            self.thumbnails.push(images[image])
          }
        }, function (errorObject) {
          console.log('The read failed: ' + errorObject.code)
        })
      },
      cancelCreateImage () {
        this.imageSelect = ''
        this.imageUrl = ''
      },
      onCreateImage () {
        const imageData = {
          title: this.imageTitle,
          imageUrl: this.imageUrl,
          description: this.imageDescription
        }
        console.log(imageData)
        firebase.database().ref('images').push().set(imageData)
          .then((data) => {
            this.cancelCreateImage()
          })
          .catch((err) => {
            console.log(err)
          })
      },
      onFilePicked (event) {
        const file = event.target.files
        let fileName = file[0].name
        if (fileName.lastIndexOf('.') <= 0) {
          return console.log('please add valid file')
        }
        const fileReader = new FileReader()
        fileReader.addEventListener('load', () => {
          this.imageUrl = fileReader.result
        })
        fileReader.readAsDataURL(file[0])
        this.imageSelect = file[0]
      },
      onPick () {
        this.$refs.fileInput.click()
      }
    },
    updated: function () {
      this.imageGet()
    },
    mounted: function () {
      console.log(this.imageData)
    }
  }
</script>