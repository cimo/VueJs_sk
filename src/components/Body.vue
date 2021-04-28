<template>
    <div class="component_body">
        <p>{{ message }}</p>
    </div>
</template>

<script lang="ts">
    import { Component, Vue } from "vue-property-decorator";

    @Component({
        components: {}
    })

    export default class ComponentBody extends Vue {
        // Variables
        private message: string = "cimo";

        // Hooks
        public created(): void {
            window.addEventListener("load", this.logicLoadEvent, { passive: true });
            window.addEventListener("resize", this.logicResizeEvent, { passive: true });
        }

        public destroyed(): void {
            window.removeEventListener("load", this.logicLoadEvent, false);
            window.removeEventListener("resize", this.logicResizeEvent, false);

            document.removeEventListener("click", this.logicClickEvent, false);
            document.removeEventListener("dblclick", this.logicDoubleClickEvent, false);
        }

        // Logic
        private logicLoadEvent(): void {
            document.addEventListener("click", this.logicClickEvent, { passive: true });
            document.addEventListener("dblclick", this.logicDoubleClickEvent, { passive: true });
            document.addEventListener("change", this.logicChangeEvent, { passive: true });
        }

        private logicResizeEvent(): void {}

        private logicClickEvent(): void {}

        private logicDoubleClickEvent(): void {}

        private logicChangeEvent(): void {}
    }
</script>

<style scoped lang="scss">
    .component_body {}
</style>
