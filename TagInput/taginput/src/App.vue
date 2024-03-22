<script>
  import InputTag from "./components/InputTag.vue";
  export default{
    components:{
      InputTag,
    },
    data(){
      return{
        etiquetas: [],
      }
    },
    methods:{
      handleOnTagsChange(tags){
        console.log(tags);
        this.etiquetas = tags;
      },
    },
  };

</script>

<template>
  <div class="contenedor">
    <h3>Input que crea tags</h3>
    <div class="ComponentInputTag">
      <InputTag @OnTagChange="handleOnTagsChange"/>
    </div>
    <h3>Regreso tags</h3>
    <ul class="listado">
      <div v-for="(tag,index) in etiquetas" :key="index">
          <li>
            {{ tag }}
          </li>
      </div>
  
    </ul>
  </div>
</template>

<style scoped>
.contenedor{
  display: flex;
  flex-direction: column;
  justify-content: center;
  background-color: #ffd3ca;
  height:100vh;
  padding: 15px;
}
h3{
  text-align: center;
  padding-top: 5px;
  font-weight:bold;
  color: #6153cb;
}
.listado{
  display: flex;
  flex-direction: column;
  align-items: center;
}
.ComponentInputTag{
  display: flex;
  justify-content: center;
}
</style>
