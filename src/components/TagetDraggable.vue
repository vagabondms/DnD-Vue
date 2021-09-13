<template>
  <div ref="target" draggable="true" @dragstart="dragStart" @dragend="dragEnd" @drag="drag" class="size-1" :class= "{ dragging : isDragging }" >
    <div>
      <v-icon @mouseover="hover">mdi-drag-horizontal</v-icon>
    </div>
    <div  class="contents">
      Target
    </div>
      
  </div>
</template>

<script>

/* <로직>
  1. HTML의 draggable을 사용함.
  2. target을 드래그 했을 때, 기존 element의 display 속성을 none으로 바꾸어 제거함.
  3. target을 드래그 한 상태로 다른 element 위로 마우스를 올렸을 때,
    3-1. 해당 element의 앞에 div element(placeholder)를 생성.
    3-2. placeholder 위에서 drag 되고 있는 target이 빠져나가면, placeholder 삭제
*/
// draggable 를 사용해서 display none으로 바꿈 
// 만약 옮겼을때 placeholder 위에 올라간다면 얘를 제거하면서 이 위치에 얘를 넣으면된다. 
// 아니면 다시 diplay =block으로 바꾼다. 

export default {
  data(){
    return {
      isDragging : false,
    }
  },
  methods:{
    hover(){

    },
    //dragstart가 트리거 되면, drag-on이라는 이벤트를 발생시킨다. 
    dragStart(){
      this.$emit('drag-on')
    },
    // dragStrat에 바로 display="none"을 시키면 바로 element가 사라지기 때문에 dragEnd가 트리거 된다. 
    // 따라서 drag event가 트리거 될 때 display none을 해주어야 한다.
    //? 두 함수를 합쳐도 될 것 같긴한데 확실하지 않아서 일단 분리한다.
    drag(){
      this.isDragging = true
    },
    dragEnd(){
      //dragstart가 트리거 되면, drag-on이라는 이벤트를 발생시킨다. 
      //또한 isDragging이라는 class를 제거한다.
      this.$emit('drag-off')
      this.isDragging = false;
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
.dragging {
  display: none;
}
</style>