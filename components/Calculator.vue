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
        <button class="bg-blue-600 text-white rounded-full py-3 px-12 hover:scale-110 transition">
          Calcular
        </button>
      </div>
    </form>
    <div  class="animate-fadeIn my-20">
      <div class="flex justify-center px-6" >
        <div class="relative rounded-full border-gray-300 border-4 py-4 w-full md:w-1/2 px-4">
          <div class="absolute bottom-14 left-1/2 transform -translate-x-1/2 bg-white px-6">
            <p class="text-lg font-semibold text-[#30323A]" >Resultado</p>
          </div>
          <p class="text-3xl font-semibold text-center text-[#30323A]">Total de paneles: {{ this.resultado }}</p>
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
    };
  },
  methods: {
    calcular() {
      const fit1 = Math.floor(this.anchoTecho / this.anchoPanel) * Math.floor(this.largoTecho / this.largoPanel);
      const fit2 = Math.floor(this.anchoTecho / this.largoPanel) * Math.floor(this.largoTecho / this.anchoPanel);
      return this.resultado = Math.max(fit1, fit2);
},

    resetForm() {
      this.anchoTecho = null,
      this.largoTecho = null,
      this.anchoPanel = null,
      this.largoPanel = null
    }
  },
};
</script>