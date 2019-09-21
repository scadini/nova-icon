<template>
    <div class="flex border-b border-40">
        <div class="w-1/4 py-4">
            <slot>
                <h4 class="font-normal text-80">{{ field.name }}</h4>
            </slot>
        </div>
        <div class="w-3/4 py-4 break-words">
            <component
                :is="componentInstance"
                class="fill-current"
                :class="field.css"
                v-if="field.show">
            </component>
        </div>
    </div>
</template>

<script>
export default {
    props: ['resource', 'resourceName', 'resourceId', 'field'],

    computed: {
        componentInstance() {
            return require(`./vendor/entypo/${this.field.icon}`);
        }
    }
}
</script>
