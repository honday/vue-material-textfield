<template>
    <div class="v-textfield">
        <div class="v-textfield-content">
            <input type="text" class="v-textfield-form" :class="{empty: isEmpty}" v-model="text">
            <p class="v-textfield-labels">
                <span class="v-textfield-label">{{ label }}</span>
                <span class="v-textfield-placeholder" :class="{hidden: !isEmpty}">{{ placeholder }}</span>
            </p>
        </div>
    </div>
</template>

<script>
    export default {
        props: {
            label: {
                type: String,
                default: () => { return ''; }
            },
            placeholder: {
                type: String,
                default: () => { return ''; }
            },
            value: {
                type: String,
                default: () => { return ''; }
            }
        },
        data () {
            return {
                text: ''
            };
        },
        methods: {
            created : function () {
                this.text = this.value;
            }
        },
        computed: {
            isEmpty: function () {
                return this.text === undefined || this.text === "";
            }
        }
    }
</script>

<style>
.hidden {
    opacity: 0 !important;
}
.v-textfield {
    display: inline-block;
    width: 300px;
    font-size: 16px;
    font-family: "Meiryo UI", monospace;
}
.v-textfield * {
    font-family: inherit;
    font-size: inherit;
    margin: 0;
    padding: 0;
}
.v-textfield .v-textfield-content {
    position: relative;
}
.v-textfield .v-textfield-form {
    background-color: transparent;
    border: none;
    outline: none;
    width: 100%;
    position: absolute;
    bottom: 0;
    margin-bottom: 5px;
}
.v-textfield .v-textfield-labels {
    display: block;
    pointer-events: none;
    position: relative;
    bottom: 0;

    padding-bottom: 5px;
}
.v-textfield .v-textfield-labels::after {
    content: "";
    display: block;
    height: 0;
    width: 100%;
    border: none;
    border-bottom: 2px solid rgb(0, 188, 212);
    position: absolute;
    bottom: 0;
}
.v-textfield .v-textfield-label {
    display: inline-block;
    width: 100%;
    pointer-events: none;
}
.v-textfield .v-textfield-placeholder {
    display: inline-block;
    border: none;
    width: 100%;
}
.v-textfield-labels {
    width: 100%;
}

.v-textfield-form + .v-textfield-labels,
.v-textfield-form:focus + .v-textfield-labels,
.v-textfield-form + .v-textfield-labels::after,
.v-textfield-form:focus + .v-textfield-labels::after,
.v-textfield-form + .v-textfield-labels > .v-textfield-label,
.v-textfield-form:focus + .v-textfield-labels > .v-textfield-label,
.v-textfield-form + .v-textfield-labels > .v-textfield-placeholder,
.v-textfield-form:focus + .v-textfield-labels > .v-textfield-placeholder {
    transition: all .2s ease-out;
}

.v-textfield-form + .v-textfield-labels {
    border-bottom: 1px solid #e0e0e0;
}
.v-textfield-form:focus + .v-textfield-labels {
    border-bottom: 1px solid rgba(0, 0, 0, 0);
}
.v-textfield-form + .v-textfield-labels::after {
    transform: scaleX(0);
}
.v-textfield-form:focus + .v-textfield-labels::after {
    transform: scaleX(1);
}
.v-textfield-form:not(.empty) + .v-textfield-labels > .v-textfield-label {
    font-size: 75%;
    transform: translateY(0);
}
.v-textfield-form + .v-textfield-labels > .v-textfield-label {
    color: rgba(0, 0, 0, 0.24);
    transform: translateY(100%);
    font-size: inherit;
}
.v-textfield-form:focus + .v-textfield-labels > .v-textfield-label {
    transform: translateY(0);
    color: rgb(0, 188, 212);
    font-size: 75%;
}
.v-textfield-form + .v-textfield-labels > .v-textfield-placeholder {
    opacity: 0;
}
.v-textfield-form:focus + .v-textfield-labels > .v-textfield-placeholder {
    opacity: 0.24;
}

</style>
