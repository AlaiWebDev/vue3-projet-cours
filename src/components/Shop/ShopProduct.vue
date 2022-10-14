<script setup lang="ts">
    import type { ProductInterface } from '@/interfaces';

    defineProps<{
        product: ProductInterface;
    }>();
    const emit = defineEmits<{
        (e: 'addProductToCart', productId: number): void;
    }>();
</script>

<template>
    <div class="product d-flex flex-column">
        <div
            class="product-image"
            :style="{ backgroundImage: `url(${product.image})` }"
        ></div>
        <div class="p-10 d-flex flex-column bottom-div">
            <h4>{{ product.title }}</h4>
            <p>{{ product.reference }}</p>
            <div class="d-flex flex-row align-items-center">
                <strong class="d-flex flex-fill">Prix : {{ product.price.toFixed(2) }}€</strong>
                <button
                    class="btn ml-10 btn-primary"
                    @click="emit('addProductToCart', product.id)"
                    v-if="product.stock !==0"
                >
                Ajouter au panier
                </button>
                <button
                    class="btn ml-10 btn-disabled"
                    v-else
                >
                STOCK ÉPUISÉ
                </button>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.product {
    width: fit-content;
    background-color: #F2C48D;
    border: var(--border);
    border-radius: var(--border-radius);
    &-image {
        border-top-right-radius: var(--border-radius);
        border-top-left-radius: var(--border-radius);
        background-size: cover;
        background-position: center;
        height: 250px;
    }
    .bottom-div {
        width: 225px;
        height: 10rem;
    }
}
</style>