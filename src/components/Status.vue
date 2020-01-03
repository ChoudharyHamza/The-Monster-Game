<template>
    <div  class="col" style="margin-top:30px; border: 1px solid #888888; box-shadow:2px 2px #888888">
      <div  v-for="(item,index) in playerDamage" :key="index+'b'" >
      <div id="player-dam" > {{item}} </div>
      <div id="monster-dam"> {{monsterDamage[index]}} </div>
    </div>
    </div>
</template>

<script>
export default {
    props:{
      playerDamage:Function,
      monsterDamage:Function
      },
    data(){
        return{
        
        }
    },
    

}
</script>



<style>
#player-dam{
  background-color: rgb(88, 209, 169);
  display: block;
  margin:10px;
}
#monster-dam{
  background-color: rgb(167, 68, 68);
  display: block;
  margin:10px;
}
</style>