<template>
  <section>
    <form @submit.prevent="calcular" class="space-y-10 px-10 md:px-0">
      <div class="flex justify-center w-full gap-10">
        <input
          v-model="largoTecho"
          placeholder="Largo del techo"
          type="number"
          class="rounded-full text-gray-400 ring-8 ring-gray-300 focus:outline-none w-full md:w-1/3 p-2.5"
          required
        />
        <input
          v-model="anchoTecho"
          placeholder="Ancho del techo"
          type="number"
          class="rounded-full text-gray-400 ring-8 ring-gray-300 focus:outline-none w-full md:w-1/3 p-2.5"
          required
        />
      </div>
      <div class="flex justify-center gap-10">
        <input
          v-model="largoPanel"
          placeholder="Largo del panel"
          type="number"
          class="rounded-full text-gray-400 ring-8 ring-gray-300 focus:outline-none w-full md:w-1/3 p-2.5"
          required
        />
        <input
          v-model="anchoPanel"
          placeholder="Ancho del panel"
          type="number"
          class="rounded-full text-gray-400 ring-8 ring-gray-300 focus:outline-none w-full md:w-1/3 p-2.5"
          required
        />
      </div>
      <div class="flex justify-center">
        <button type="button" @click="resetForm" v-if="resultado !== null" class="bg-blue-600 text-white rounded-full py-3 px-12 hover:scale-110 transition" >
          volver a calcular
        </button>
        <button type="submit"  v-else class="bg-blue-600 text-white rounded-full py-3 px-12 hover:scale-110 transition">
          Calcular
        </button>
      </div>
    </form>
    <div v-if="resultado !== null" class="animate-fadeIn py-10">
      <div class="flex justify-center px-6" >
        <div class="absolute  md:w-1/3">
          <div class="border-gray-300 border-4 py-2  px-4" >
            <div class="absolute -top-3 left-1/2 transform -translate-x-1/2 bg-white px-6">
              <p class="text-lg font-semibold text-[#30323A]" >Resultado</p>
            </div>
            <div class="py-6 w-full" >
              <p class="text-lg font-semibold text-center text-[#30323A]" >El área del techo es: {{ this.areaTecho }} (m2)</p>
              <p class="text-lg font-semibold text-center text-[#30323A]" >El área del panel es: {{ this.areaPanel }} (m2)</p>
              <p class="text-3xl font-semibold text-center text-[#30323A]">Total de paneles: {{ this.resultado }}</p>
  
            </div>

          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      anchoTecho: null,
      largoTecho: null,
      anchoPanel: null,
      largoPanel: null,
      resultado: null,
      areaTecho: null,
      areaPanel: null
    };
  },
  methods: {
    calcular() {
      this.areaTecho = this.anchoTecho * this.largoTecho;
      this.areaPanel = this.anchoPanel * this.largoPanel

      const orientacion1 = (this.anchoTecho / this.anchoPanel).toFixed(0) * (this.largoTecho / this.largoPanel).toFixed(0);
      const orientacion2 = (this.anchoTecho / this.largoPanel).toFixed(0) * (this.largoTecho / this.anchoPanel).toFixed(0);
      this.resultado = Math.max(orientacion1, orientacion2);
    },

    resetForm() {
      this.anchoTecho = null,
      this.largoTecho = null,
      this.anchoPanel = null,
      this.largoPanel = null,
      this.areaTecho = null,
      this.areaPanel = null,
      this.resultado = null
    }
  },
};
</script>