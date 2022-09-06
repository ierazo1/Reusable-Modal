<script setup>
    //imports
    import View1 from './Views/View1.vue';
    import View2 from './Views/View2.vue';
    import View3 from './Views/View3.vue';

    //props
    const props = defineProps({modalObject: Object});

    //emits
    const emit = defineEmits(['closeModal']);    

    function selectView(targetModal)
    {
        switch(targetModal){
            case "View1":
                return View1;
                break;
            case "View2":
                return View2;
                break;
            case "View3":
                return View3;
                break;
            default:
                break;
        }
    }
</script>

<template>
    <teleport to="body">
        <transition>
            <div v-if="modalObject.isModalActive" id="backdrop" v-on:click.stop.prevent="emit('closeModal')">
                <transition>
                    <!-- Dynamic component -->
                    <!-- https://vuejs.org/api/sfc-script-setup.html#using-components -->
                    <component id="component" :is="selectView(modalObject.targetModal)"/>
                </transition>
            </div>
        </transition>
    </teleport>
</template>

<style scoped>
#backdrop {
    position: fixed;
    z-index: 998;
    top: 0; right: 0; bottom: 0; left: 0;
    background-color: rgba(0,0,0,.5);
}

#component {
  position: fixed;
  z-index: 9999;
  top: 20%;
  left: 50%;
  width: 300px;
  margin-left: -150px;
}
</style>


