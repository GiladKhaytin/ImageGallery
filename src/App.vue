<script lang="ts">

import { ref } from 'vue';

export default {

  setup() {
    const images = [
      {

        name: 'Youtube',
        src: 'Youtube.png'

      },
      {

        name: 'Instagram',
        src: 'Instagram.jpg'

      },
      {
        name: 'Facebook',
        src: 'Facebook.png'

      },
    ];

    const isModalOpen = ref(false);
    const modalImage = ref('');

    const showModal = (src: string) => {
      isModalOpen.value = true;
      modalImage.value = '/public/assets/'+src;
    };

    const closeModal = () => {
      isModalOpen.value = false;
    };

    return {

      images,
      isModalOpen,
      modalImage,
      showModal,
      closeModal,

    };
  },
}

</script>

<template>

  <div id="app" class="text-center">

    <div class="containerIcons">
      <h3 class="mt-10 mb-5 text-3xl">Image Gallery App</h3>
      <div class="container2">
        <img class="w-full h-full object-cover cursor-pointer" v-for="image in images" :src="'/public/assets/' + image.src" @click="showModal(image.src)">
      </div> 
    </div>

    <div v-if="isModalOpen" id="modal" class="fixed top-0 left-0 z-80 w-screen h-screen bg-black/70 flex justify-center items-center">
      <a class="fixed z-90 top-6 right-8 text-white text-5xl font-bold" href="javascript:void(0)"@click="closeModal">×</a>
      <img id="modal-img" class="max-w-[800px] max-h-[600px] object-cover" :src="modalImage">
    </div>
  </div>
</template>

<style scoped>


h3 {
  
  font-family: 'Courier New', Courier, monospace;
  font-size: 50px;
  font-weight: bolder;
  text-align: center;
  margin-bottom: 20px;

}

.containerIcons {
  display: flex;
  flex-direction: column;
}

.container2{
  display: flex;
  justify-content: center;
  
}

.container2 img {

  width: 200px;
}

.container2 img:hover {

  transform: scale(1.1);

}

#modal img {
  max-width: 90%;
  max-height: 80%;
  object-fit: contain;
}

</style>
