<template>
  <div>
    <form v.on:submit.prevent="add">
      <input types="text" v-model="text.text" />
        <input type="submit" value="Add" />
    </form>
  </div>
</template>

<script>
import Firebase from 'firebase'
import toastr from 'toastr'
let config={
    apiKey: "AIzaSyDrlDqZfYbo-ANLogqTFYUmezsJKGIHWoI",
    authDomain: "fir-vue-35c9b.firebaseapp.com",
    projectId: "fir-vue-35c9b",
    storageBucket: "fir-vue-35c9b.appspot.com",
    messagingSenderId: "389682140502",
    appId: "1:389682140502:web:283c601973fe3691d532f7"

}

let app = Firebase.initializeApp(config)
let db = app.database()
let textRef = db.ref('text')
export default{
  name: 'app', firebase:{
    texts : textRef
  },
  data(){
    return{
      text:{
        text:''
      }
    }
  },
  methods:{
    add: function(){
      textRef.push(this.text)
      this.text.text
      toastr.success('Added')
    }
  }
}
</script>
