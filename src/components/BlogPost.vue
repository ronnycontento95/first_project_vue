<script setup>
defineProps({
    title: String,
    id: Number,
    body: {
        type: String,
        default: "Sin descripción",
    },
    fijarFavorito: Function,
});

// defineProps(["title", "id", "body", "fijarFavorito"]);
</script>

<template>
    <div class="card">
        <div class="card-body">
            <h5 class="card-title">{{ title }}</h5>
            <p>{{ body }}</p>
            <button
                class="btn btn-sm btn-outline-primary"
                @click="fijarFavorito(title)"
            >
                Mi Favorito
            </button>
        </div>
    </div>
</template>