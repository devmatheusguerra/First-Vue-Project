<template>
  <div id="buttons-layer">
    <button class="run" v-on:click="toggleStatus(1)" v-if="status === 0">
        Iniciar
    </button>
    <button class="stop" v-on:click="toggleStatus(2)" v-if="status === 1">
        Parar
    </button>
    <button class="continue" v-on:click="toggleStatus(1)" v-if="status === 2">
        Continuar
    </button>
    <button class="refresh" v-on:click="toggleStatus(0)" v-if="status === 2">
        Zerar
    </button>
  </div>
</template>

<script>
export default {
  name: 'Buttons',
  data() {
    return {
      status : 0
    }

  },
  methods:{
    toggleStatus (status) {
      this.status = status;
      this.$emit('toggle', {status:this.status});
      }


  }

}
</script>


<style scoped>
  #buttons-layer{
    width: 100vw;
    height: 50vh;
    display: flex;
    align-items: center;
    justify-content: center;
    background: #3d3d44;
    color: white;
    font-size: 2.5rem;
    position: absolute;
    overflow: hidden;
    top: 50vh;
  }

  #buttons-layer > button {
    width: fit-content;
    padding: 1.5vh 2vh;
    border: 0;
    color: #fff;
    border-radius: 2px;
    font-weight: bolder;
    font-size: 1.5rem;
    cursor: pointer;
  }

  .stop {
    background-color: #8d0000;
  }

  .run {
    background-color: #008d00;
  }

  .continue {
    background-color: #00658d;
  }

  .refresh {
    background-color: #d85600;
    margin-left: 10px;
  }

</style>
