<template>
    <button @click="sendData">
        {{ variant }}
        <slot></slot>
        <slot name="icon"/>
    </button>
</template>

<script>
export default {

    props:{
        variant:{
            type:String,
            default:'Success'
        }
    },

    // setup(props,contexto) {
    //     console.log(contexto)
    // }
    setup(props,{slots,emit}) {
        console.log(slots)

        const sendData = () =>{

            // emit('update','chupa')
            emit('update',props.variant)
        }

        return {
            sendData
        }
    }
}

</script>