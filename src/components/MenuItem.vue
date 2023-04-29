<template>
    <div class="menu-item">
        <img
                class="menu-item__image"
                :src="image.source"
                :alt="image.alt"/>
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
                    @btnEvent="addToShoppingCart(quantity)"
                    class="btn-blue"
                >
                    {{ btnText.toUpperCase() }}
                </MyButton>
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
        addToShoppingCart: {
            type: Function,
            required: true,
            default: () => {},
        },
        name: {
            type: String,
            required: true,
            default: "name",
        },
        image: {
            type: Object,
            required: true,
        },
        price: {
            type: Number,
            required: true,
        },
        quantity: {
            type: Number,
            required: true,
        },
        inStock: {
            Boolean,
            required: true,
        }
    },
    data() {
        return {
            onSale: false,
            btnText: "Ajouter au panier"
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
        today % 2 === 0 ? this.onSale = true : this.onSale = false
    }
}
</script>

<style scoped lang="scss">
.btn-blue {
  background-color: #032551;
  color: #fff;
}

.menu-item {
  display: flex;
  width: 500px;
  justify-content: space-between;
  margin-bottom: 30px;

  &__image {
    max-width: 300px;
    border-radius: 5px;
    -webkit-box-shadow: 0px 10px 13px -7px #000000, 5px 5px 15px 5px rgba(0, 0, 0, 0);
    box-shadow: 0px 10px 13px -7px #000000, 5px 5px 15px 5px rgba(0, 0, 0, 0);
  }
}
</style>