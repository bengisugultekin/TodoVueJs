<template>
  <div id="sidebar">
       <Slide class="sidebar" disableCloseOnEsc>
        <a id="home" href="#">
            <span>Home</span>
        </a>
    </Slide>    
  </div>
</template>

<script>
import { Slide } from 'vue-burger-menu'
export default {
  name: 'sidebar',
  components: {    
    Slide
  }
}
</script>

<style>
.bm-overlay {
      background: white;
    }
</style>