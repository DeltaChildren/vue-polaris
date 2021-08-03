<template>
<div class="Polaris-TextField__Spinner"
     @click="onClick"
     aria-hidden>
    <div role="button"
         class="Polaris-TextField__Segment"
         tabindex="-1"
         @click="handleStep(1)">
        <div class="Polaris-TextField__SpinnerIcon">
            <polaris-icon source="caretUp">
            </polaris-icon>
        </div>
    </div>
    <div role="button"
         class="Polaris-TextField__Segment"
         tabindex="-1"
         @click="handleStep(-1)">
        <div class="Polaris-TextField__SpinnerIcon">
            <polaris-icon source="caretDown">
            </polaris-icon>
        </div>
    </div>
</div>
</template>

<script>
import PolarisIcon from './PolarisIcon.vue';

export default {
    components: {
        PolarisIcon,
    },
    methods: {
        onClick() {
            this.$emit('click');
        },
        handleStep(value) {
            this.$emit('change', value);
        }
    }
};
</script>