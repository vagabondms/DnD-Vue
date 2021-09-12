<template>
  <div class="size-1">
    <v-icon>mdi-drag-horizontal</v-icon>
    <div class="contents">

      <slot></slot>
    </div>
      
  </div>
</template>

<script>
export default {
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