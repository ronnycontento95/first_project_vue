<script setup>
// const props = defineProps(["title", "id", "body", "]);

defineProps({
    title: String,
    id: Number,
    colorText: String,
    body: {
        type:String,
        default: "Sin descripcion",
    }
});


</script>

<template>
    <div class="card">
        <div class="card-body">
            <h5 class="card-title">{{ title }}</h5>
            <p>{{ id }} {{ body }}</p>
            <button class="btn btn-sm btn-outline-primary" @click="fijarFavorito(title)">
                Mi Favorito
            </button>
        </div>
    </div>
</template>