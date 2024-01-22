<template>
  <div class="modal" v-if="showModal">
    <div class="modal-content">
      <p>Modal Content for ID {{ routeParams.id }}</p>
      <button @click="closeModal">Close Modal</button>
    </div>
  </div>
</template>

<script>
import { reactive, ref, onMounted, watch } from 'vue'
import { useRoute } from 'vue-router'

export default {
  name: 'Modal',
  setup() {
    const showModal = ref(false)
    const routeParams = reactive({
      id: null
    })

    const route = useRoute()

    const openModal = () => {
      showModal.value = true
    }

    const closeModal = () => {
      showModal.value = false
    }

    onMounted(() => {
      // Watch for changes in the route params and open the modal accordingly
      watch(
        () => route.params,
        (params) => {
          routeParams.id = params.id
          openModal()
        },
        { immediate: true }
      )
    })

    return {
      showModal,
      routeParams,
      closeModal
    }
  }
}
</script>

<style scoped>
.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(255, 0, 0, 0.2);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 99;
}

.modal-content {
  background: white;
  padding: 20px;
}
</style>
