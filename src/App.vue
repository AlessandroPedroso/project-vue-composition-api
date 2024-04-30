<template>
  <h3>Usando Computed()</h3>
  {{ fullName }}
  <br>
  <h5>Admin Utilizando Função</h5>
  {{ user.first_name }} - {{ user.last_name }}
  <br>
  <button @click="user.first_name = 'Eduardo Pedroso'">Atualizar</button>
  <br>
  <br>
  <br>
  <AppHook v-if="showAppHook"/>
  <button @click="showAppHook = !showAppHook">Toggle</button>
  <br>
  <br>
  <br>
  <AppButton :variant="danger" @update="getUpdate"  data-vue="Alessandro">Save <template #icon>Icon</template></AppButton>
</template>

<script>
import { computed, ref, watch } from 'vue';
import AppHook from './components/AppHook.vue'
import AppButton from './components/AppButton.vue'

export default {
  name: 'App',
  components: {
    AppHook,
    AppButton
  },

  setup() {

    //ref utiliza o value para modificar o seu valor na reactividade
    const user = ref({
      first_name: 'AdminAlessandro',
      last_name: 'Pedroso'
    })

    // recomenda-se utilizar sempre o ref
    const count = ref(0)
    const testeString = ref('Alessandro')
    console.log(testeString)
    console.log(count)
    ////////////////
    const changeName = () => {
      alert('chegou')
      //utilizando ref, precisa chamar o '.value'
      user.value.first_name = 'XXXX'
    }

    const showAppHook = ref(true)

    //Computed e watch
    const fullName = computed(() => {
      return `${user.value.first_name} ${user.value.last_name}`
    })

    // //quando alterar o objeto usuario ele vai imprimir
    // watch(user,()=>{
    //   alert('Watch alterou o objeto')
    // },{
    //   deep:true
    // })

    //quando alterar a propriedade usuario ele vai imprimir
    watch(()=>user.value.first_name, () => {
      alert('Watch, alterou o first_name')
    })

    //pegando o emit do componente filho AppButton

    const getUpdate = (data)=>{
      console.log('getUpdate:', data)
    }


    return {
      changeName,
      user,
      fullName,
      showAppHook,
      getUpdate
    }

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
