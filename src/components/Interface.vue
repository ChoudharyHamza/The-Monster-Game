<template>
    <div>
    <div class="row" style="margin-top:80px">

      <div class="col-sm" > 

        <h1><b> You </b></h1>

        <div id="nonhealth-bar" class="col wid"><div id="health-bar" class="col wid" :style="displayPlayerBar"> {{ playerHealth }} </div></div>
      </div>

      <div class="col-sm"  > 

        <h1><b>Monster</b></h1>

        <div id="nonhealth-bar" class="col wid"><div id="health-bar" class="col wid"  :style="displayMonsterBar" > {{ monsterHealth }} </div></div>
      </div>

    </div>
    <buttons :monsterDam="monsterDam" :playerDam="playerDam" :startGame="startGame" :start="start" :onGiveUp="onGiveUp" :onHeal="onHeal"></buttons>

    <status v-show="displayStatus" :playerDamage="playerDamage" :monsterDamage="monsterDamage"  ></status>
    </div>

</template>


<script>
/* eslint-disable */
import Buttons from "./Buttons"
import Status from "./Status"
export default {
    components:{
        buttons:Buttons,
        status:Status
    },
    data(){
        return{
            startGame:false,
            playerHealth:100,
            monsterHealth:100,
            currentPlayer:0,
            currentMonster:0,
            playerDamage:[],
            monsterDamage:[]
        }
    },
    methods:{

        randomValue(n){
          return Math.ceil(Math.random()*n);
        },
    
        
        playerDam(){
          let val = this.randomValue(10);
          this.playerHealth -= val; 
          this.currentMonster = val;
          this.matchWon();
        },
        monsterDam(n){
          let val = this.randomValue(n);
          this.monsterHealth-=val;
          this.currentPlayer= val;
          this.matchWon();
        },

        start(){
        this.startGame = true;
        
        },

        onGiveUp(){
            this.startGame=false;
            this.playerHealth=100;
            this.monsterHealth=100;
            this.currentPlayer=0;
            this.currentMonster=0;
            this.playerDamage=[];
            this.monsterDamage=[]          
        },
        matchWon(){
          if(this.playerHealth<=0){
            alert("You Lost!  better luck next time");
          }
          if(this.monsterHealth<=0)
          {
            alert("You Have Won! congts");
          }
        },

      onHeal(){
        let val = this.randomValue(20);
        let health = this.playerHealth + val;
        if(health<100)
        {
        this.playerHealth += val;
        this.currentPlayer = val;
        }
        this.playerDam(10);
        },
    },
    watch:{
        currentPlayer:function(){
            this.playerDamage.unshift(this.currentPlayer);
        },
        currentMonster:function(){
            this.monsterDamage.unshift(this.currentMonster);
        }
    },
    computed:{
      displayPlayerBar(){
        return {
          width:this.playerHealth+"%"
        }
      },
      displayMonsterBar(){
        return{
          width:this.monsterHealth+"%"
        }
      },
      displayStatus(){
        return this.monsterDamage.length > 0
      }

    }
}
/* eslint-disable */
</script>

<style scoped>


#nonhealth-bar{
  background-color:grey;
}

#health-bar{
  background-color: green;
   
}

.wid{

  padding:0px;
  font-size: 25px
}


</style>