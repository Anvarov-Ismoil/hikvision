<template>
  <div class="modal w-full max-w-[750px] bg-white mx-auto py-3 p-5 rounded-md shadow-md">

    <!-- modal-content -->
    <div class="modal-content" v-if="!isInfoSent">
      <!-- close -->
      <div class="close flex items-center justify-end">
        <h3 class="text-3xl font-semibold text-center flex-grow">Отправить данные</h3>
        <button class="text-black/80 text-4xl" @click="$emit('action')">
          <i class="fa-solid fa-xmark "></i>
        </button>
      </div>
      <!-- content -->
      <div class="content">
        <form class="form my-5 sm:my-10 w-full sm:w-3/4 mx-auto" @submit.prevent="sendData">
          <div class="input-box flex flex-col justify-center">
            <p class="text-xl" :class="{ 'text-red-500': isEmpty && !modalData.name }">Ваше имя</p>
            <input id="name" type="text"
              class="border-b border-black py-1 pl-1 pr-5 mt-3 text-xl focus:outline-black/70" v-model="modalData.name">
            <label for="name" class="text-lg text-red-600 mb-2 opacity-0"
              :class="{ 'opacity-100': isEmpty && !modalData.name }">
              Поле не должно быть пустым!
            </label>
          </div>
          <div class="input-box flex flex-col justify-center">
            <p class="text-xl" :class="{ 'text-red-500': isEmpty && !modalData.number }">Ваш номер</p>
            <input id="number" type="number"
              class="border-b border-black py-1 pl-1 pr-5 mt-3 text-xl focus:outline-black/70"
              v-model="modalData.number">
            <label for="number" class="text-lg text-red-600 mb-2 opacity-0"
              :class="{ 'opacity-100': isEmpty && !modalData.number }">
              Поле не должно быть пустым!
            </label>
          </div>
          <div class="btn-box mt-3 md:mt-7">
            <button class="btn border-2 border-brand-color hover:bg-brand-color text-brand-color hover:text-white transition-all rounded-full
            text-xl py-3 px-10 w-full" @click="sendData">
              Отправить
            </button>
          </div>
        </form>
      </div>
    </div>

    <!-- thx -->
    <div class="thx" v-else>
      <!-- close -->
      <div class="close flex items-center justify-end">
        <!-- <h3 class="text-3xl font-semibold text-center flex-grow">Отправить данные</h3> -->
        <button class="text-black/80 text-4xl" @click="$emit('action')">
          <i class="fa-solid fa-xmark "></i>
        </button>
      </div>
      <!-- content -->
      <div class="text mt-5 mb-10">
        <h4 class="text-2xl text-center my-1">Ваша информация отправлена.</h4>
        <h4 class="text-2xl text-center my-1">Мы свяжемся с вами в ближайшее время!</h4>
      </div>
    </div>

  </div>
</template>

<script>
export default {
  data() {
    return {
      modalData: {
        name: '',
        number: ''
      },
      isEmpty: false,
      isInfoSent: false,
    }
  },
  methods: {
    sendData() {
      if (this.modalData.name === '' || this.modalData.number === '') {
        this.isEmpty = true
      } else {
        this.isEmpty = false
        this.isInfoSent = true
      }
    }
  }
}
</script>

<style scoped>
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

input[type=number] {
  -moz-appearance: textfield;
}
</style>