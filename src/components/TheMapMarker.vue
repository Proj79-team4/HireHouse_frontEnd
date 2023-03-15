<template>
    <div >
        <div id='map' ref="mapRef"></div>
    </div>
</template>

<script>
import { onMounted, ref } from 'vue'; 
export default { 
  name: 'Map', 
  setup() { 
    const mapRef = ref(null); 
    onMounted(() => { 
       
            const tt = window.tt; 
            var map = tt.map({ 
            key: '6hakT8QU7IRSx9PCHGi5JyHTV2S7xWlD', 
            container: mapRef.value, 
            style: 'tomtom://vector/1/basic-main', 
        }); 
        map.addControl(new tt.FullscreenControl()); 
        map.addControl(new tt.NavigationControl());  
    }) 
 
    return { 
      mapRef, 
    }; 
  }  
}
</script>

<style lang="scss" scoped>
 
#map { 
    height: 50vh; 
    width: 50vw; 
} 
</style>