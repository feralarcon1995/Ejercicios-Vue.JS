<template>
  <div>
    <ul class="list-group ">
      <li v-for="(item,index) of ordernar" :key="item.id"
        class="list-group-item d-flex justify-content-between align-items-start"
      @click="aumentar(index)">
        {{index}} - {{item.nombre}}
        <span class="badge bg-primary rounded-pill">{{item.cantidad}}</span>
      </li>
     
    </ul>
     <button class="btn btn-danger w-100 mt-2" @click="reiniciar">Reiniciar</button>
  </div>
</template>

<script>

import {mapState, mapMutations} from 'vuex';

export default {
  name: "Lista",
  computed: {
      ...mapState(['frutas']),
      ordernar(){
          return this.frutas.sort( (a,b) => b.cantidad - a.cantidad )
      }
  },
  methods:{
      ...mapMutations(['aumentar','reiniciar'])
      
    
  }
};
</script>