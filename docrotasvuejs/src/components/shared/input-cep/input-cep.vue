<template>
    <input 
        class="el-input__inner" 
        v-bind="$props" 
        :value="currentValue" 
        @input="handleInput"
        v-mask="'##.###-###'"
        maxlength="10">
    </input>
</template>
<script>
    export default {
        name: 'DrtInputCep',
        componenteName: 'DrtInputep',
        data () {
            return {
                currentValue: this.value
            }
        },
        methods: {
            handleInput(event) {
                const value = event.target.value;
                this.$emit('input', value);
                this.setCurrentValue(value);
                this.$emit('change', value);
            },
            setCurrentValue(value) {
                if (value === this.currentValue) return;
                this.currentValue = value;
            }
        },
        props: {
             value : String
        },
        watch: {
            'value'(val, oldValue) {
                this.setCurrentValue(val);
            }
        }
    }
</script>
<style>

</style>