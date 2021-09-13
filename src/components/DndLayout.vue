<template>
  <div class="dnd-layout" >
      <dnd-draggable1 :isDragging="isDragging">
          <template>1</template>
      </dnd-draggable1>
      <dnd-draggable1>
          <template>2</template>
      </dnd-draggable1>
      <target-draggable @drag-on="dragOn" @drag-off="dragOff" />
      <dnd-draggable1 :isDragging="isDragging">
          <template>3</template>
      </dnd-draggable1>
      <dnd-draggable2>
          <template>Large 1</template>
      </dnd-draggable2>
      <dnd-draggable1>
          <template>4</template>
      </dnd-draggable1>
      <dnd-draggable1>
          <template>5</template>
      </dnd-draggable1>
      <dnd-draggable2>
          <template>Large 2</template>
      </dnd-draggable2>
      <dnd-draggable1>
          <template>6</template>
      </dnd-draggable1>
        
  </div>
</template>

<script>
import DndDraggable1 from "./DndDraggable1.vue"
import DndDraggable2 from "./DndDraggable2.vue"

import TargetDraggable from "./TagetDraggable.vue"



export default {
    data(){
        return {
            isDragging : false
        }
    },
    methods:{
        
        dragOn(){
            console.log('on')
            this.isDragging = true
        },
        dragOff(){
            console.log('off')
            this.isDragging = false
        },

    },
    components:{
        DndDraggable1,
        DndDraggable2,
        TargetDraggable,
    }
}
</script>

<style scoped>
.dnd-layout{
    display:grid;
    /* 행의 개수는 동적으로 변한다. */
    grid-auto-rows: minmax(50px,auto);
    /* 열의 개수는 2로 고정, 크기는 auto 
    TODO: 나중에 바꿀 필요가 있다.
    */
    grid-template-columns: repeat(2, minmax(45%, auto));
    
    gap: 10px 10px;
    /* column을 기준으로 쌓인다. */
    
}

</style>
 