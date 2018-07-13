<template>
    <v-app dark>
        <v-content>
            <v-container>
                <nuxt />
            </v-container>
        </v-content>
        <v-footer :fixed="fixed" app>
            <span>The Footer!</span>
        </v-footer>
    </v-app>
</template>

<script>
export default {
    data() {
        return {
            fixed: false,
            title: 'Vuetify.js',
        };
    },
};
</script>
