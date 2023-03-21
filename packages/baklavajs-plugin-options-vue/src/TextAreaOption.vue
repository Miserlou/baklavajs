<template>
    <div>
        <textarea
            type="text"
            class="dark-input"
            :value="value"
            v-on="listeners"
            :placeholder="name"
        ></textarea>
    </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class TextAreaOption extends Vue {

    @Prop({ type: String, default: "" })
    value!: string;

    @Prop({ type: String })
    name!: string;

    get listeners(): any {
        return { ...this.$listeners, input: (ev: any) => this.$emit("textarea", ev.target.value) };
    }

}
</script>
