<template>
    <button
            :type="btnType"
            :class="btnClass"
            @click="emitEvent">
        {{ text }}
    </button>
</template>

<script>
export default {
    name: "MyButton",
    props: {
        text: {
            type : String,
            default: "Button",
            required: true,
        },
        btnType: {
            type: String,
            default: "button",
        },
        btnClass: {
            type: String,
            default: "btn",
        },

    },
    emits: {
        click : null,
    },
    methods: {
        emitEvent() {
            this.$emit('btnEvent')
        }
    }
}
</script>

<style scoped>
.btn {
    width: 100%;
    border: solid 1px black;
    border-radius: 2px;
    margin: 1rem auto;
    padding: 1rem;
    background-color: aqua;
}

</style>