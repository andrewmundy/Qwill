<template>
    <div class="company">
      <main/>
      hi
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
              images
            }"
          />
        </transition>
      </div>
    </div>
</template>

<script>
  export default {
    name: 'Message',
    props: [
      'edit',
      'fbInfo',
      'toggle',
      'firebase',
      'requireAuth'
    ],
    data () {
      return {

      }
    },
    methods: {
    }
  }
</script>

<style lang="scss">
    .company{
      color:black;
    }
    @media screen and (max-device-width: 1024px) {
      .company{
        
      }
    }
  </style>