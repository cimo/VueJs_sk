<template>
    <div class="body_component">
        <p>{{ message }}</p>
    </div>
</template>

<script lang="ts">
    import { Component, Vue } from "vue-property-decorator";

    @Component
    export default class Body extends Vue {
        private message: string = "cimo";

        private loadEvent(): void {
            document.addEventListener("click", this.clickEvent, { passive: true });
            document.addEventListener("dblclick", this.doubleClickEvent, { passive: true });
            document.addEventListener("change", this.changeEvent, { passive: true });
        }

        private clickEvent(): void {}

        private doubleClickEvent(): void {}

        private changeEvent(): void {}

        private resizeEvent(): void {}

        public created(): void {
            window.addEventListener("load", this.loadEvent, { passive: true });
            window.addEventListener("resize", this.resizeEvent, { passive: true });
        }

        public mounted(): void {}

        public updated(): void {}

        public beforeDestroy(): void {
            window.removeEventListener("load", this.loadEvent, false);
            window.removeEventListener("resize", this.resizeEvent, false);

            document.removeEventListener("click", this.clickEvent, false);
            document.removeEventListener("dblclick", this.doubleClickEvent, false);
        }
    }
</script>

<style scoped lang="scss">
    .body_component {
    }
</style>
