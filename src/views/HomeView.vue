<template>
    <div class="home">
        <h1>{{ restaurantName }}</h1>
        <p class="description">
            Bienvenue dans notre café {{ restaurantName }}! Nous sommes réputés pour
            notre pain et nos merveilleuses pâtisseries. Faites vous plaisir dès le
            matin ou avec un goûter réconfortant. Mais attention, vous verrez qu'il
            est difficile de s'arrêter.
        </p>

        <section class="menu">
            <h2>Menu</h2>
            <MenuItem
                    v-for="item in simpleMenu"
                    :add-to-shopping-cart="addToShoppingCart"
                    :name="item.name"
                    :image="item.image"
                    :price="item.price"
                    :quantity="item.quantity"
                    :in-stock="item.inStock"
                    :key="item.name"

            />
        </section>

        <aside class="shopping-cart">
            <h2>Panier d'achat : {{ shoppingCart }} articles</h2>
        </aside>
    </div>
</template>

<script>
// @ is an alias to /src
import MenuItem from "@/components/MenuItem.vue";
// import sourceData from "@/sourceData.json";

export default {
    name: 'HomeView',
    components: {
        MenuItem,
    },
    data() {
        return {
            shoppingCart: 0,
            simpleMenu: [
                {
                    name: "Croissant",
                    image: {
                        source: "/images/croissant.jpg",
                        alt: "Un croissant"
                    },
                    inStock: true,
                    price: 2.99,
                    quantity: 1
                },
                {
                    name: "Baguette de pain",
                    image: {
                        source: "/images/french-baguette.jpeg",
                        alt: "Quatre baguettes de pain"
                    },
                    inStock: true,
                    price: 3.99,
                    quantity: 1
                },
                {
                    name: "Éclair",
                    image: {
                        source: "/images/eclair.jpg",
                        alt: "Éclair au chocolat"
                    },
                    inStock: false,
                    price: 4.99,
                    quantity: 1
                }
            ]
        }
    },
    // computed: {
    //     copyright() {
    //         const currentYear = new Date().getFullYear()
    //
    //         return `Copyright ${this.restaurantName} ${currentYear}`
    //     }
    // },
    methods: {
        addToShoppingCart(amount) {
            this.shoppingCart += amount
        }
    }
}
</script>
