<template>
    <div id="app">
        <nav>
            <NavLink url="/" text="Accueil"/>
            <NavLink url="/about" text="A propos"/>
            <NavLink url="/contact" text="Contact"/>
        </nav>
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
                :quantity="item.quantity"
                :in-stock="item.inStock"
                :key="item.name"

            />
        </section>

        <aside class="shopping-cart">
            <h2>Panier d'achat : {{ shoppingCart }} articles</h2>
        </aside>

        <h2>Contactez nous</h2>
        <p>Adresse : {{ address }}</p>
        <p>Téléphone : {{ phone }}</p>
        <p>Email : {{ email }}</p>
        <p>Horaires :</p>
        <ul>
            <li>L-V: 06:00 à 16:00</li>
            <li>Samedi: 07:00 à 14:00</li>
            <li>Dimanche: 07:00 à 12:00</li>
        </ul>
        <footer class="footer">
            <p>{{ copyright }}</p>
        </footer>

    </div>

</template>

<script>
import NavLink from "@/components/NavLink.vue";
import MenuItem from "@/components/MenuItem.vue";

export default {
    name: 'App',
    components: {
        MenuItem,
        NavLink,
    },
    data() {
        return {
            address: "18 avenue du Beurre, Paris, France",
            email: "hello@cafewithavue.bakery",
            phone: "01 88 88 88 88",
            restaurantName: "La belle vue",
            shoppingCart: 0,
            simpleMenu: [
                {
                    name: "Croissant",
                    image: {
                        source: "/images/croissant.jpg",
                        alt: "Un croissant"
                    },
                    inStock: true,
                    quantity: 1
                },
                {
                    name: "Baguette de pain",
                    image: {
                        source: "/images/french-baguette.jpeg",
                        alt: "Quatre baguettes de pain"
                    },
                    inStock: true,
                    quantity: 1
                },
                {
                    name: "Éclair",
                    image: {
                        source: "/images/eclair.jpg",
                        alt: "Éclair au chocolat"
                    },
                    inStock: false,
                    quantity: 1
                }
            ]
        }
    },
    computed: {
        copyright() {
            const currentYear = new Date().getFullYear()

            return `Copyright ${this.restaurantName} ${currentYear}`
        }
    },
    methods: {
        addToShoppingCart(amount) {
            this.shoppingCart += amount
        }
    }
}
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
