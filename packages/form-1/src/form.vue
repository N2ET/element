<template>
    <form class="el-form" :class="[
        labelPosition ? 'el-form--label-' + labelPosition : '',
        { 'el-form--inline': inline }
      ]">
        <slot></slot>
    </form>
</template>
<script>
export default {
    name: 'ElForm',

    componentName: 'ElForm',

    props: {
        model: Object,
        rules: Object,
        labelPosition: String,
        labelWidth: String,
        labelSuffix: {
            type: String,
            default: ''
        },
        inline: Boolean
        // showMessage: {
        //     type: Boolean,
        //     default: true
        // }
    },
    watch: {
        // rules() {
        //     this.validate();
        // }
    },
    data() {
        return {
            fields: [],
            rules: {
                '#id': {
                    minValue: 100,
                    maxValue: 1000,
                    validator () {},
                    cb () {}
                }
            }
        };
    },
    created() {
        this.$on('el.form.addField', (field) => {
            if (field) {
                this.fields.push(field);
            }
        });
        /* istanbul ignore next */
        this.$on('el.form.removeField', (field) => {
            if (field.prop) {
                this.fields.splice(this.fields.indexOf(field), 1);
            }
        });
    },
    methods: {
        resetFields() {
            if (!this.model) {
                process.env.NODE_ENV !== 'production' &&
                    console.warn('[Element Warn][Form]model is required for resetFields to work.');
                return;
            }
            this.fields.forEach(field => {
                field.resetField();
            });
        },

        validate(callback) {
            
        },

        validateField(prop, cb) {
            
        },

        getRule() {

        },

        addRule() {

        },

        removeRule() {

        }


    }
};
</script>
