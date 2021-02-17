<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-buttons slot="start">
          <ion-menu-button color="primary"></ion-menu-button>
        </ion-buttons>
        <ion-title>{{ $route.params.id }}</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">{{ $route.params.id }} </ion-title>
        </ion-toolbar>
      </ion-header>

      <div id="container">

          <h1>Add a new member</h1>

        <form class="ion-padding" expand="block" ref="form">

          <div id="space"/>

          <ion-label>Name</ion-label>
          <ion-item>
            <ion-input v-model="name" ></ion-input>
          </ion-item>

          <div id="space"/>

          <ion-label>Gender</ion-label>
            <ion-radio-group v-model="gender">
              <ion-item>
                <ion-label>Male</ion-label>
                  <ion-radio slot="start" value="male"></ion-radio>
              </ion-item>

              <ion-item>
                <ion-label>Female</ion-label>
                <ion-radio  slot="start" value="female"></ion-radio>
              </ion-item>
            </ion-radio-group>

            <div id="space"/>

            <ion-label>Info</ion-label>
            <ion-item>
              <ion-textarea rows="7" v-model="info" ></ion-textarea>
            </ion-item>

           <div id="space"/>

            <ion-label>Accept</ion-label>
            <ion-radio-group v-model="accept" value="yes">
              <ion-item>
                <ion-label>Yes</ion-label>
                  <ion-radio slot="start" value="yes"></ion-radio>
              </ion-item>

                <ion-item>
                  <ion-label >No</ion-label>
                  <ion-radio  slot="start" value="no"></ion-radio>
                </ion-item>
            </ion-radio-group>

            <div id="space"/>
            
            <!--pass data from the inputs to the function -->
            <ion-button @click="submit(name, gender, info, accept)">Save New Member</ion-button>

        </form>
      </div>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonButtons,actionSheetController, alertController, IonInput, IonItem,  IonLabel, IonList,  IonListHeader, IonRadioGroup, IonContent, IonHeader, IonMenuButton, IonPage, IonTitle, IonToolbar } from '@ionic/vue';
import {useRoute} from "vue-router";
import {ref, onMounted, defineComponent } from 'vue';


export default defineComponent({
  name: 'Folder',
  components: {
    IonButtons,
    IonContent,
    IonHeader,
    IonItem,
    IonInput,
    IonMenuButton,
    IonPage,
    IonTitle,
    IonToolbar
  },

  //Data from the inputs
  data(){
    return{
      name:"",
      gender:"",
      info:"",
      accept:"",
    };
  },

  setup(){

    const route=useRoute();


    return{
      route
      };
    },

    methods: {

    //get data from the inputs/form
    submit:function(name: any, gender: any, info: any, accept: any){
        //display data from the inputs/form
        console.log(name);
        console.log(gender);
        console.log(info);
        console.log(accept);
        console.log("New memebr has been saved.\nName: "+ name+"\n"+"gender: "+gender+"\n"+"info: "+ info+"\n"+"accepted "+accept);
    },

  },
})

</script>

<style scoped>

#space{
  margin-top:71px;
  margin-bottom:31px;
}

#container {

  text-align: center;
  left: 0;
  right: 0;
  margin-top: 53px;
  margin-bottom:53px;

}

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
/*  font-size: 16px;*/
  line-height: 22px;
/*   color: #8c8c8c;*/
  /*margin: 0;*/
}

#container a {
  text-decoration: none;
}
</style>
