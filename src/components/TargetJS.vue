<template>
  <div draggable=true   @dragenter="hi" id="target" ref="target"  class="size-1" >
    <div>
      <v-icon>mdi-drag-horizontal</v-icon>
    </div>
    <div  class="contents">
      Target
    </div>
  </div>
</template>

<script>


export default {
  methods:{
    hi(){
      this.$refs.target.style.display = "none"
    },
    dragAndDrop(e){
      console.log('hi')
      const draggable = this.$refs.target
      const curWidth = draggable.clientWidth
      const curHeight = draggable.clientHeight
      const { style } = draggable

      // 현재 element의 x/y 좌표
      const {x,y} = draggable.getBoundingClientRect()

      style.position ="absolute"
      style.zIndex = 1000;
      style.width = curWidth + 2 + 'px'
      style.height = curHeight + 2 +'px' 

      const xGap = e.pageX-x
      const yGap = e.pageY-y
      
      const onMouseMove = (e) => {
        const {pageX, pageY} = e
        style.left = pageX - xGap + 'px'
        style.top = pageY - yGap + 'px'
      }
      document.addEventListener("mousemove", onMouseMove)

      draggable.onmouseup = () => {
        document.removeEventListener("mousemove", onMouseMove)
        draggable.onmouseup = null
      }
    },
    createDiv(){
      const grid = this.$refs.target.parentElement
      const newDiv = document.createElement('div')
      newDiv.classList.add('placeholder')
      
      const deletePlaceHolder = ()=>{
          document.querySelector('.placeholder').remove()
      } 
      newDiv.addEventListener('mouseleave', deletePlaceHolder)
      grid.insertBefore(newDiv, this.$refs.target)
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