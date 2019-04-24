<template>
  <div id="app">
    <Home v-if="!isLogin"></Home>
    <Editor v-if="isLogin"></Editor>
  </div>
</template>

<script>
import Home from "./componemts/Hom.vue";    
import Editor from "./componemts/Editor.vue";    

export default{
  name: "app",
  data(){
    return{
      isLogin: false,
      userData: null
    };
  },
created: function(){
  firebase.auth().onAuthStateChanged(user =>{
    console.log(user);
    if (user){
      this.isLogin = true;
      this.userData = user;
    }else{
      this.isLogin = false;
      this.userData = null;
    }
  });
},

  components:{
  Home: Home,
  editor: Editor
  }
};
</script>  