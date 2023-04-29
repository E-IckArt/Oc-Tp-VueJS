<template>
    <div class="menu-item">
        <img
            class="menu-item__image"
            :src="image.source"
            :alt="image.alt" />
        <div>
            <h3>{{ name }}</h3>
            <p>Prix : {{ generatedPrice }}</p>
            <p v-if="inStock">En stock</p>
            <p v-else>En rupture de stock</p>
            <div>
                <label for="add-item-quantity">
                    Quantité : {{ quantity }}
                </label>
<!--                TODO - Bugfix v-model-->
<!--                <input-->
<!--                    v-model.number="quantity"-->
<!--                    id="add-item-quantity"-->
<!--                    type="number"-->
<!--                />-->
                <MyButton
                    text="Ajouter au panier"
                    @btnEvent="addToShoppingCart(quantity)" />
            </div>
        </div>
    </div>

</template>

<script>

import MyButton from "@/components/MyButton.vue";

export default {
    name: "MenuItem",
    components: {MyButton},
    props: {
        addToShoppingCart: Function,
        name : String,
        image: Object,
        price: Number,
        quantity: Number,
        inStock: Boolean,
    },
    data() {
        return {
            onSale: false
        }
    },
    computed: {
        generatedPrice() {
            if (this.onSale) {
                return (this.price * 0.9).toFixed(2)
            } else {
                return this.price;
            }
        }
    },
    beforeMount() {
        const today = new Date().getDate()
        today %2 === 0 ? this.onSale = true : this.onSale = false
    }
}
</script>

<style scoped>

</style>