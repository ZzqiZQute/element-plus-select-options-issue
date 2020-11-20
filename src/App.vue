<template>
    <div id="app">
        <el-form>
            <el-form-item>
                <el-select
                        :model-value="model"
                        @change="handleChange"
                        multiple
                        value-key="value"
                        @visible-change="handleVisibleChange"
                >
                    <el-option v-for="item in options"
                               :key="item.key"
                               :label="item.value"
                               :value="item"
                    >
                    </el-option>
                </el-select>
            </el-form-item>
        </el-form>
    </div>
</template>

<script lang="ts">
    import { ref, defineComponent } from 'vue';

    export default defineComponent({
        setup () {
            const options = ref<Record<any, any>[]>([]);
            const model = ref<Record<any, any>[]>([]);
            const handleChange = (item: any) => {
                model.value = item;
            };
            const handleVisibleChange = (visible: boolean) => {
                if (visible) {
                    options.value = Array.from({length: 5}).map((_, i) => ({key: '' + i, value: '' + i}))
                }
            };
            return {
                model,
                options,
                handleChange,
                handleVisibleChange
            };
        }
    });
</script>

<style>
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }
</style>
