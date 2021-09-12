<template>
  <div ref="target" draggable="true" @drag="drag"  class="size-1" >
    <div>
      <v-icon @mousedown.self="dragAndDrop" @mouseup="null">mdi-drag-horizontal</v-icon>
    </div>
    <div  class="contents">
      Target
    </div>
      
  </div>
</template>

<script>

// draggable 를 사용해서 display none으로 바꿈 
// 만약 옮겼을때 placeholder 위에 올라간다면 얘를 제거하면서 이 위치에 얘를 넣으면된다. 
// 아니면 다시 diplay =block으로 바꾼다. 

export default {
  
  methods:{
    drag(e){

    }
  }
}
</script>

<style scoped>
.size-1{
  border: 1px solid lightblue;
  grid-column : auto / span 1;
  display:flex;
  flex-direction:column;
  
}
</style>