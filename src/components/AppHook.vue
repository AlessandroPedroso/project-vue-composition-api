<template>
    <div>
        Hook
    </div>
</template>

<script>
import {onBeforeMount,onMounted,onBeforeUnmount,onUnmounted} from 'vue'
export default {
    //setup ja é a fase de criação no caso utilizando OptionAPi era o created(), nesse caso compositionAPI usando o setup()
    setup() {

        onBeforeMount(()=>{
            console.log('onBeforeMount')
        })

        onMounted(()=>{
            console.log('onMounted')
        })

        onBeforeUnmount(()=>{
            console.log('onBeforeUnmount')
        })

        onUnmounted(()=>{
            console.log('onUnmounted')
        })
    }
}

</script>