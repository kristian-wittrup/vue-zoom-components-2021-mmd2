<template>
  <v-container>
    <!--
    <div>
      <p>{{ hello }}</p>
      <button @click="changeContent()">
        Click me
      </button>
    </div>
    -->
    <!-- Toggle basic : This will toggle all with same v-if 
    <div v-if="showContent">
      <p> {{ title }} </p>

    </div>
    <div v-if="showContent">
      <p> {{ titleTwo }} </p>

    </div>
    -->
    <!--
    <button @click="toogleContent">
      Show/hide content
    </button>-->

    

<!-- Toggle Individual item start -->

    <div v-for="item in memesLib" :key="item.index">
      <div v-show="item.toogleInd">
        <p>{{ item.memeTitle }}</p>
        <img :src="item.imgStuff" alt="" height=200>
        <button @click="toggleInd(item)">Click</button>
      </div>
      <div v-if="!item.toogleInd">
        MNeeee
      </div>
    </div>




  </v-container>
</template>

<script>
  export default {
    name: 'HelloWorld',

    data: () => ({
/* 
      hello: "Say hello to Homer",
      title : "Show me da money",
      titleTwo : "Im freeee",
      showContent: true
*/      
    
    memesLib: [
      {
        memeTitle : "Show me the cat",
        imgStuff: require('../assets/vibe.gif'),
        toogleInd: false
      },
      {
        memeTitle : "Show me the dog",
        imgStuff: require('../assets/dogcar.gif'),
        toogleInd: true
      },
      
    ]

    }),
    methods: {
      toggleInd(item) {
        item.toggleInd = !item.toggleInd
     
      },
      toogleContent() {
        this.showContent = !this.showContent
      },
      changeContent() {
        this.hello = "Say hello to Grandpa"
      }
    }
  }
</script>
