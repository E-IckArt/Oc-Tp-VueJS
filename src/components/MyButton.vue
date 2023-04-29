<template>
    <button
            :type="btnType"
            :class="btnClass"
            @click="emitEvent">
        <slot></slot>
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
    cursor: pointer;
    width: 100%;
    border: solid 1px black;
    border-radius: 2px;
    margin: 1rem;
    padding: 1rem;
    font-weight: bold;
    -webkit-box-shadow: 0px 10px 13px -7px #000000, 5px 5px 15px 5px rgba(0,0,0,0);
    box-shadow: 0px 10px 13px -7px #000000, 5px 5px 15px 5px rgba(0,0,0,0);
}

</style>