<template>
    <footer class="footer">
        <nav>
            <NavLink url="/" text="Accueil"/>
            <NavLink url="/about" text="A propos"/>
            <NavLink url="/contact" text="Contact"/>
        </nav>
        <p>{{ copyright }}</p>
    </footer>

</template>

<script>
import NavLink from "@/components/NavLink.vue";

export default {
    name: "AppFooter",
    components: {NavLink},
    data() {
        return {
            restaurantName: "La belle vue",
        }
    },
    computed: {
        copyright() {
            const currentYear = new Date().getFullYear()

            return `Copyright ${this.restaurantName} ${currentYear}`
        }
    },
}
</script>

<style scoped>

</style>