<template>
  <div class="size-1" ref="target" @dragover="createDiv">
    <v-icon>mdi-drag-horizontal</v-icon>
    <div class="contents">

      <slot></slot>
    </div>
      
  </div>
</template>

<script>
export default {
  props:{
    isDragging : {
      type : Boolean,
    require : true,
    }
    
  },
  methods:{
    createDiv(){
      if(this.isDragging){
        const grid = this.$refs.target.parentElement
        const newDiv = document.createElement('div')
        newDiv.classList.add('placeholder')
        
        const deletePlaceHolder = ()=>{
          document.querySelector('.placeholder').remove()
        } 
        newDiv.addEventListener('dragleave', deletePlaceHolder)
        grid.insertBefore(newDiv, this.$refs.target)
      }
      
    },
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

<style>
.placeholder{
  background-color: gainsboro;
  opacity: 0.5;
}
</style>