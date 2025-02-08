<template>
  <div class="h-screen font-mont" >
    <div class="max-w-[1000px] mx-auto md:px-10" >
      <div class="flex justify-center items-center w-full p-6" >
        <img src="/images/logo/logo.svg" alt="Ruuf" class="">
      </div>
      <div class="flex flex-col justify-center items-center my-10" >
        <h1 class="text-4xl md:text-7xl font-semibold text-[#30323A] text-center" >Calculadora</h1>
        <h2 class="text-4xl md:text-7xl font-semibold text-center text-gradient">paneles solares</h2>
      </div>
      <div>
        <Calculator />
      </div>
    </div>
  </div>
</template>

<style>
.text-gradient {
  background-image: linear-gradient(90deg, #ebcf4d, #64b6e5, #5a6ed5);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
}
</style>