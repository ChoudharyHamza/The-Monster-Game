<template>
    <div claas="row" style="margin-top:30px; border: 1px solid #888888; box-shadow:2px 2px #888888">

      <div v-if="startGame" ><button v-for="item in buttons" @click="item.func" :key="item.id" class="ali btn" :class="item.type" > {{item.name}} </button>
      </div>
      <button v-else class="ali btn btn-primary" @click="start" > Start Game </button>

    </div>
</template>

<script>


export default { 
  props:{
    monsterDam:Function,
    playerDam:Function, 
    startGame:Function,
    start:Function,
    onGiveUp:Function,
    onHeal:Function},
  data(){
     return{
          buttons:[
            {name:"Attack", type:"btn-danger",id:1, func : this.onAttack },
            {name:"Speacial Attack", type:"btn-warning",id:2, func :this.onSpeacial },
            {name:"Heal Up", type:"btn-success",id:3, func:this.onHeal},
            {name:"Give up", type:"btn-dark",id:4 ,func:this.onGiveUp }
            ]
     };
  },
  methods:{
    
    onAttack(){
      this.playerDam();
      this.monsterDam(10);
    },

    onSpeacial(){
      this.playerDam();
      this.monsterDam(14);
    },

    
  }

}

</script>

<style scoped>

.ali{

  margin:20px;
  font-size: 20px;
}

</style>