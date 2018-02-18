<template>
    <div>
      <div class="font-window">
        <ul id="fonts">
        <i style="font-size:0.5rem;">Here are some popular fonts.</i>
        <li @click="pickFont(fontInstance, 'Roboto')">Roboto</li>
        <li @click="pickFont(fontInstance, 'Yellowtail')">Yellow Tail</li>
        <li @click="pickFont(fontInstance, 'Lobster')">Lobster</li>
        <li @click="pickFont(fontInstance, 'Impact')">Impact</li>
        <li @click="pickFont(fontInstance, 'Quicksand')">Quicksand</li>
        <li @click="pickFont(fontInstance, 'Merriweather')">Merriweather</li>
        <li @click="pickFont(fontInstance, 'Fantasy')">Papyrus(dont)</li>

        <i style="font-size:0.5rem;">Choose a Google Font</i>
        <li v-for="font in fonts" @click="pickFont(fontInstance, font)" v-bind:key="font">
          {{font}}
        </li>
        </ul>
      </div>
      <div class="font-import">
        Import Google Font
        <i style="font-size:0.5rem;">or <a href="https://fonts.google.com/">find</a> a Google Font and type it below</i>
        <input 
          v-model="account.public.events[21208].fontImport"
          v-on="fontImport = account.public.events[21208].fontImport"
        >
        <button class="" @click="pickFont(fontInstance, account.public.events[21208].fontImport)">import</button>
      </div>
    </div>
</template>

<style lang="scss">
    .font-import{
      display: flex;
      justify-content: center;
      flex-direction: column;
      width:auto;
      button{
        background:rgba(255,255,255,0.2);
        border-radius: 4px;
        padding:4px;
        margin: 2px;
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
        .font-window{
          width:auto;
          // padding:5px;
          *{
            border-radius: 5px;
            margin: 6px 0px 6px 0px;
          }
        }
        .font-import{
          padding:5px;
        }
      }
    }
</style>

<script>
  export default {
    name: 'FontPicker',
    props: [
      'toggle',
      'fbInfo',
      'fontColor',
      'fontStyle',
      'fontImport',
      'importFont',
      'fonts',
      'fontSort',
      'account',
      'titleFont',
      'descriptionFont',
      'fontInstance'
    ],
    data () {
      return {
        fontImport: ''
      }
    },
    methods: {
      whichFontSort (sort) {
        this.fontSort = sort
      },
      createNode (element) {
        return document.createElement(element)
      },
      append (parent, el) {
        return parent.appendChild(el)
      },
      pickFont: function (rule, fontFamily) {
        console.log(rule, fontFamily)
        let fontFamilyRule = rule
        let parsedFont = fontFamily.replace(/\b[a-z]/g, function (f) {
          return f.toUpperCase().split(' ').join('+')
        })
        this.account.public.events[21208][fontFamilyRule] = parsedFont
        this.account.public.events[21208].fontImport = fontFamily
        this.fontInstance = rule
      }
    },
    updated: function () {
    }
  }
</script>