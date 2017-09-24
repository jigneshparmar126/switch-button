<template>
    <label class="switch">
        <input :class="classes" type="checkbox" :checked="checked" :name="name" :disabled="disabled" v-model="value" @change.stop="change(value)">
        <span :class="{'active': value}">
            <slot>
                   <span class="off" :class="{'hide': value}"></span>
                   <span class="on" :class="{'hide': !value}"></span>
            </slot>
        </span>
    </label>
</template>
<script>
    export default {
        props: {
            disabled: Boolean,
            classes: String,
            checked: Boolean,
            name: String
        },
        data() {
            return {
                value: null
            }
        },
        beforeMount() {
            this.value = this.checked
        },
        mounted() {
            this.$emit('input', this.value)
        },
        watch: {
            value(val) {
                this.$emit('input', val)
            },
            checked (val) {
                this.value = val
            }
        },
        methods:{
            change(obj,value){
                this.$emit('change',obj,value) ;
            }
        }
    }
</script>
<style lang="scss">
    label.switch {
        input[type="checkbox"] {
            display: none;
            &:checked {
                + span {
                    &:before {
                        background-color: rgba(230,232,233,1);
                    }
                    &:after {
                        background-color:#FFF;
                        transform: translate(17px, -12px);
                    }
                }
            }
            + span {
                position: relative;
                display: inline-block;
                cursor: pointer;
                font-weight: 500;
                text-align: left;
                margin: 0px;
                padding: 0px 44px;
                &:before,
                &:after {
                    content: '';
                    cursor: pointer;
                    position: absolute;
                    margin: 0;
                    outline: 0;
                    top: 50%;
                    transform: translate(0, -50%);
                    transition: all 200ms ease-out;
                }
                &:before {
                    left: 1px;
                    width: 48px;
                    height: 32px;
                    background-color: rgba(230,232,233,1);
                    border-radius: 16px;
                }
                &:after {
                    left: 4px;
                    width: 25px;
                    height: 25px;
                    background-color:#FFF;
                    border-radius: 50%;
                    box-shadow: 0 3px 1px -2px rgba(0, 0, 0, .14), 0 2px 2px 0 rgba(0, 0, 0, .098), 0 1px 5px 0 rgba(0, 0, 0, .084);
                }
            }
            &:checked + span &:after {
                transform: translate(80%, -50%);
            }
        }
    }
</style>
<style>
    label{
        cursor: pointer;
    }
    label.switch .active span.on{
        content: '';
        position: absolute;
        width: 6px;
        height: 10px;
        -webkit-transform: rotate(45deg);
        transform: rotate(45deg);
        top: -6px;
        z-index: 1;
        left: 30px;
        -webkit-transition: top ease-in-out .25s;
        transition: top ease-in-out .25s;
    }
    label.switch input[type="checkbox"] + span.active:after{
        background:#fff !important;
    }
</style>
