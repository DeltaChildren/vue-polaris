<template>
<div>
    <div>
        <ul class="Polaris-Tabs" role="tablist">
            <li v-for="name in tabNames" class="Polaris-Tabs__TabContainer" role="presentation">
                <button
                    @click="loadActiveTab(name)"
                    :class="{'Polaris-Tabs__Tab':1, 'Polaris-Tabs__Tab--selected': activeTab == name}"
                    role="tab"
                    tabindex="-1">
                    <span class="Polaris-Tabs__Title">{{ name }}</span>
                </button>
            </li>
        </ul>
    </div>
    <div v-for="name in tabNames" style="padding: 1.6rem;" v-if="name == activeTab">
        <slot :name="name"></slot>
    </div>
</div>
</template>



<script>
export default {
    model: {
        prop: 'value',
        event: 'change'
    },
    props: [
        'value'
    ],
    data() {
        return {
            activeTab: null
        }
    },
    mounted() {
        this.loadActiveTab(this.tabNames[0]);
    },
    computed: {
        tabNames() {
            return this.value;
        }
    },
    methods: {
        loadActiveTab(name) {
            this.activeTab = name;
            this.$emit('change', this.activeTab);
        }
    }
}
</script>
