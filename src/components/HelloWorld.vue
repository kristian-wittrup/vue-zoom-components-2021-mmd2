<template>
  <v-container>
     <!-- Grabbing dynamic data from the variable "hello", the data object -->
    <div class="pa-4">
      <p>{{ hello }}</p>
      <v-btn dark @click="changeContent()"> <!-- invoking/calling the function(method) called changeContent -->
        Click me
      </v-btn>
    </div>
    <hr>
    <!-- Toggle basic : This will toggle all with same v-if -->
    <div class="pa-4" v-if="showContent"> <!-- show/hide if its true/falase -->
      <p> {{ title }} </p>
    </div>
    <div class="pa-4" v-if="showContent">
      <p> {{ titleTwo }} </p>
    </div>
    <v-btn class="red mb-4" @click="toogleContent"> <!-- Toogle state(true/false) of toogleContent through the method called toogleContent -->
      Show/hide content
    </v-btn>
    <hr>

    

<!-- Toggle Individual item :: start -->
  <div class="mt-4" v-for="item in memesLib" :key="item.id"  >  <!-- For Loop to print item, and have an uniq identifier to toogle false/true -->
    <div v-show="item.toggleInd"> <!-- Show or hide element based of toggleInd is either true or false -->
      <h4>{{ item.memesTitle }}</h4> 
      <img :src="item.memesImg" height=200 alt="">
      <v-btn class="red" @click="toggleInd(item)">Hide single item</v-btn> <!-- toggleInd() method called on click : we are passing along the entire "item" so the method knows which one is clicked. (placement in array: position 0, or 1, or 2, etc) -->
    </div>
    <div v-if="!item.toggleInd"> <!-- Show or hide element based of toggleInd is either true or false -->
      <v-btn class="green" @click="toggleInd(item)">Show single item</v-btn> <!-- Button to toggle back -->
    </div>  
  </div>



  </v-container>
</template>

<script>
  export default {
    name: 'HelloWorld',

    data: () => ({

      hello: "Say hello to Homer",
      title : "Show me da money",
      titleTwo : "Im freeee",
      showContent: true, // used to hide or show an HTML element
      
    memesLib: [  // 3.2
        {
          memesTitle: 'Vibe cat', // 3.2 
          memesImg: require('../assets/vibe.gif'), // 3.2,   // Show in vueExtension without the required.
          toggleInd: true // 3.3 toggle indivual
        },
        {
          memesTitle: 'Dog in Car', // 3.2
          memesImg: require('../assets/dogcar.gif'), // 3.2
          toggleInd: true // 3.3 toggle indivual,
        }
      ],

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
