<template>
    <component
        :is="componentInstance"
        class="fill-current"
        :class="field.css"
        v-if="field.show">
    </component>
</template>

<script>
export default {
    props: ['resourceName', 'field'],

    computed: {
        componentInstance() {
            return require(`./vendor/entypo/${this.field.icon}`);
        }
    }
}
</script>
