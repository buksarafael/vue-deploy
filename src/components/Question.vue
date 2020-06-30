<template>
<div class="question-box " >
  <b-jumbotron style="background-color: rgba(245, 245, 245, 0.3); margin-top:25px; -webkit-text-stroke: 1.7px black; border-radius: 155px;" :header="heads" header-level="4">
    <template v-slot:lead>
    <div v-if="start==0">
      <b-button style="-webkit-text-stroke: 0px black;" size="lg" v-on:click="nextWaifu">START</b-button>
    </div>
    <h1 v-if="index>17 && index<20 && start==1" class="bg-light" style="margin-left:330px; margin-right:330px; border-radius: 25px " > BONUS </h1>
    <img v-if="index<20 && start==1" style="border: 15px solid black; border-radius: 105px" v-bind:src="Waifus[index].img" alt="lmao" height="430px" width="430px" />
    <div v-else-if="start==1">
    <h1> CONGRATULATIONS, YOU ARE A WEEB {{heads=""}} </h1>
    </div>
    </template>
    <div v-if="index<20 && start==1">
    <hr class="my-4">
    <input style="-webkit-text-stroke: 0px black; border-radius: 10px; background-color: rgb(230, 182, 79) " v-model="input" v-on:keyup.enter="checkWaifu" />
    <br/>
    <br/>
    <b-button style="-webkit-text-stroke: 0px black;" variant="primary" v-on:click="checkWaifu" >Next</b-button> 
    <span style="display:inline-block; width:100px;"></span>
    <b-button style="-webkit-text-stroke: 0px black;" variant="danger" v-on:click="hint">Hint</b-button>
    <br/>
    <h1>{{zahinto}}</h1>
  <h4 style="-webkit-text-stroke: 0.5px black; background-color: rgba(245, 245, 245,1); margin-left:350px; margin-right:350px; border-radius: 105px ">
    Waifu #{{index+1}} 
  </h4>
  </div>
  </b-jumbotron>
</div>
</template>
<script>      
export default {
    props:{
    },
  data(){
    return{
      Waifus:[
            {
            name: "Rem",
            img: require("@/assets/rem.jpg"),
            hint:"Re:Zero"
            },

            {
            name:"Zero Two",
            img:require("@/assets/zerotwo.jpg"),
            hint:"Darling in the Franxx"
            },

            {
            name:"Midnight",
            img:require("@/assets/midnight.jpg"),
            hint:"My Hero Academia"
            },
            {
            name: "Raphtalia",
            img: require("@/assets/raphtalia.jpg"),
            hint:"The Rise of the Shield Hero"
            },

            {
            name:"Mai Sakurajima",
            img:require("@/assets/mai.jpg"),
            hint:"Rascal Does Not Dream of Bunny Girl Senpai"
            },

            {
            name:"Uraraka",
            img:require("@/assets/uraraka.jpg"),
            hint:"My Hero Academia"
            },
             {
            name:"Chika",
            img:require("@/assets/chika.jpg"),
            hint:"Kaguya-sama Love is War"
            },
             {
            name:"Rikka Takarada",
            img:require("@/assets/rikka.jpg"),
            hint:"SSSS.Gridman"
            },
             {
            name:"Rias Gremory",
            img:require("@/assets/rias.jpg"),
            hint:"Highschool DxD"
            },
             {
            name:"Hestia",
            img:require("@/assets/hestia.jpg"),
            hint:"DanMachi"
            },
             {
            name:"Ayanami Rei",
            img:require("@/assets/rei.jpg"),
            hint:"Neon Genesis Evangelion"
            },
             {
            name:"Senjougahara",
            img:require("@/assets/senjougahara.jpg"),
            hint:"Bakemonogatari"
            },
             {
            name:"Misaki Mei",
            img:require("@/assets/misaki.jpg"),
            hint:"Another"
            },
             {
            name:"Sinon",
            img:require("@/assets/sinon.jpg"),
            hint:"Sword Art Online II"
            },
             {
            name:"Speedwagon",
            img:require("@/assets/speedwagon.jpg"),
            hint:"Jojo's Bizzare Adventure: Phantom Blood"
            },
             {
            name:"Esdeath",
            img:require("@/assets/esdeath.jpg"),
            hint:"Akame ga Kill"
            },
             {
            name:"Makise Kurisu",
            img:require("@/assets/makise.jpg"),
            hint:"Steins;Gate"
            },
             {
            name:"Megumin",
            img:require("@/assets/megumin.jpg"),
            hint:"KonoSuba"
            },
             {
            name:"Mari Ohara",
            img:require("@/assets/mari.jpg"),
            hint:"Love Live!"
            },
             {
            name:"Rui Tachibana",
            img:require("@/assets/rui.jpg"),
            hint:"Domestic Girlfriend"
            },
            
        ],
        index:-1,
        input:"",
        zahinto:"",
        hints:5,
        ok:0,
        heads:"Can you guess all the waifus?",
        start:0
    }    
  },
  methods:{ 
     nextWaifu(){
         this.index++;
         this.input="";
         this.zahinto="";
         this.ok=0;
         this.start=1;
         this.heads="Who's this waifu?"
     },
     checkWaifu(){
       if(this.input===this.Waifus[this.index].name){
         this.nextWaifu();
       }
       else{
        return false;
       }
     },
     hint(){
       if(this.hints>0&&this.ok==0){
         this.zahinto=this.Waifus[this.index].hint;
         this.hints--;
         this.ok=1;
       }

     }
  }    
}
</script>
<style>
#question-box{
color: #08a823c7;
background-color:transparent;
opacity: 0.2;
}
</style>