<template>
    <div>
        <Navbar />
        <div class="product-page">
            <h1>Productos de la Barbería</h1>
            <div class="product-grid">
                <div v-for="(product, index) in products" :key="index" class="product-card">
                    <img :src="product.image" alt="Imagen del producto" class="product-image" />
                    <div class="product-info">
                        <h2>{{ product.name }}</h2>
                        <p>{{ product.description }}</p>
                        <p class="product-price">{{ product.price | currency }}</p>
                        <button class="reserve-button">Agregar al Carrito</button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import Navbar from '../components/Navbar.vue';

export default defineComponent({
    name: 'ProductList',
    components: {
        Navbar,
    },
    setup() {
        const products = ref([
            {
                name: 'Gel de Peinado',
                description: 'Gel de alta fijación para peinados duraderos.',
                price: 15,
                image: new URL('../assets/productobarber1.jpg', import.meta.url).href,
            },
            {
                name: 'Crema para Afeitar',
                description: 'Crema de afeitar suave para una piel sin irritaciones.',
                price: 10,
                image: new URL('../assets/productobarber2.jpg', import.meta.url).href,
            },
            {
                name: 'Cera para el Cabello',
                description: 'Cera moldeadora para estilos modernos.',
                price: 12,
                image: new URL('../assets/productobarber3.jpg', import.meta.url).href,
            },
            {
                name: 'Aftershave',
                description: 'Loción refrescante para después del afeitado.',
                price: 8,
                image: new URL('../assets/productobarber4.jpg', import.meta.url).href,
            },
            {
                name: 'Aceite para Barba',
                description: 'Aceite para mantener la barba suave y saludable.',
                price: 18,
                image: new URL('../assets/productobarber5.jpg', import.meta.url).href,
            },
            {
                name: 'Champú para Cabello',
                description: 'Champú especial para mantener el cabello saludable.',
                price: 14,
                image: new URL('../assets/productobarber6.jpg', import.meta.url).href,
            },
        ]);

        return {
            products,
        };
    },
    filters: {
        currency(value: number) {
            return new Intl.NumberFormat('es-ES', {
                style: 'currency',
                currency: 'USD',
            }).format(value);
        },
    },
});
</script>

<style scoped>
.product-page {
    padding: 2rem;
    text-align: center;
}

.product-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 1.5rem;
    margin-top: 1rem;
}

.product-card {
    border: 1px solid #ddd;
    border-radius: 8px;
    overflow: hidden;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    background-color: #fff;
    text-align: left;
    transition: transform 0.3s;
}

.product-card:hover {
    transform: scale(1.05);
}

.product-image {
    width: 100%;
    height: 150px;
    object-fit: cover;
}

.product-info {
    padding: 1rem;
}

.product-info h2 {
    font-size: 1.2rem;
    margin-bottom: 0.5rem;
}

.product-price {
    font-weight: bold;
    color: #5561ff;
    margin-top: 0.5rem;
}

.reserve-button {
    background-color: #5561ff;
    color: #fff;
    padding: 0.5rem;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s;
    margin-top: 0.5rem;
    width: 100%;
}

.reserve-button:hover {
    background-color: #404dcc;
}
</style>
