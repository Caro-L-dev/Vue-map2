<template>
    <div>
        <div ref="map" style="width: 100vw; height: 100vh"></div>
    </div>
</template>

<script>

    export default {
    
        const H = windows.H;
        name: "HereMap2",
        data() {
            return {
                platform: {},
                map: {}
            }
        },
        props: {
            apiKey: String,
            latitude: String,
            longitude: String,
            zoom: String
        },
        created() {
            this.platform = new H.service.Platform({
                "apiKey": this.apiKey
            });
        },
        mounted() {
            this.map = new H.map(
                this.$refs.map,
                this.platform.createDefaultLayers().vector.normal.map,
                {
                    zoom: this.zoom,
                    center: { lat: this.latitude, lng: this.longitude}
                }
            );
        }
    }
</script>
