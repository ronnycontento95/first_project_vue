<script setup>

defineProps(["inicio", "fin", 'maxlenght']);

const emit = defineEmits(["next", "previus", "inicio", "fin"]);

const activarSiguiente = () => {
  console.log("Activar siguiente");
  emit("next");
};

</script>
<template>
  <div class="btn-group" role="group" aria-label="Basic example">
    <button
      @click="emit('previus')"
      type="button"
      class="btn btn-outline-primary"
      :disabled="inicio <= 0"
    >
      Previus {{ inicio }}
    </button>
    <button
      @click="activarSiguiente"
      type="button"
      class="btn btn-outline-primary"
      :disabled="fin >= maxlenght"
    >
      Next {{ fin }}
    </button>
  </div>
</template>
