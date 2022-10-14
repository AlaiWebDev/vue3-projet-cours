<script setup lang="ts">
    import type { ProductInterface } from '@/interfaces';
    import ShopProductList from './ShopProductList.vue';

    defineProps<{
        products: ProductInterface[];
    }>();

    const emit = defineEmits<{
        (e: 'addProductToCart', productId: number): void;
    }>();
</script>

<template>
    <div>
        <img src="../../assets/images/logo.png" alt="">
        <h2>Figurines</h2>
        <ShopProductList
        @add-product-to-cart="emit('addProductToCart', $event)"
        :products="products"
        />
    </div>
</template>

<style lang="scss" scoped>
    img {
        display: block;
        width: 20%;
        margin: auto;
        padding: 1rem;
    }

    h2 {
        text-align: center;
        font-size: smaller;
    }
</style>