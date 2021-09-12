<template>
  <div ref="ho" @mouseover="createDiv">hi</div>
</template>

<script>

export default {
  
    methods:{
        createDiv(){
            const grid = this.$refs.ho.parentElement
            const newDiv = document.createElement('div')
            newDiv.classList.add('placeholder')
            
            const deletePlaceHolder = ()=>{
                document.querySelector('.placeholder').remove()
            } 
            newDiv.addEventListener('mouseleave', deletePlaceHolder)
            grid.insertBefore( newDiv, this.$refs.ho)
        },
    }
}
</script>

<style>

</style>