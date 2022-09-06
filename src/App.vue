<script setup>
  import {ref, reactive} from 'vue';
  import ModalVue from './components/modal.vue';
  
  //modal object
  const modalObject  = reactive({
    isModalActive: false, 
    targetModal: ""
  });
  
  function toggleModal(elementID = "")
  {
    modalObject.isModalActive = !modalObject.isModalActive;
    modalObject.targetModal = elementID;
  }
</script>

<template>
  <div class="container">
    <nav class="navbar navbar-expand-lg bg-light">
      <div class="container-fluid">
        <a class="navbar-brand" href="#">DemoModal</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav">
            <li class="nav-item dropdown">
            <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown" aria-expanded="false">
              Open Modal
            </a>
            <ul class="dropdown-menu">
              <li><a class="dropdown-item" id="View1" href="#" @click="toggleModal($event.currentTarget.id)">Modal 1</a></li>
              <li><a class="dropdown-item" id="View2" href="#" @click="toggleModal($event.currentTarget.id)">Modal 2</a></li>
              <li><a class="dropdown-item" id="View3" href="#" @click="toggleModal($event.currentTarget.id)">Modal 3</a></li>
            </ul>
          </li>
          </ul>
        </div>
      </div>
    </nav> 
  </div>
  
    
   <ModalVue :modalObject="modalObject" @closeModal="toggleModal()"/> 
</template>





<style scoped>

</style>
