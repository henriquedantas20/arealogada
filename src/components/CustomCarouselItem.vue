<script setup lang="ts">
    import { ref } from 'vue'
    import CustomSelect from './CustomSelect.vue'

    const isDesktop = ref(window.screen.width >= 1024)
    
    defineProps<{
        icon: string,
        title: string,
        subtitle: string,
        options: Array<string>
    }>()

    const emits = defineEmits(["selected"])
</script>

<template>
    <div class="carousel-item-wrapper">
        <header class="carousel-item-header">
            <img :src="icon" class="carousel-item-header-icon"/>
            <div class="carousel-item-header-text">
                <span class="carousel-item-header-text-title">{{ title }}</span>
                <span class="carousel-item-header-text-subtitle">{{ subtitle }}</span>
            </div>
        </header>
        <div class="carousel-item-options">
            <div class="carousel-item-options-wrapper" v-if="isDesktop">
                <CustomSelect  
                    :options="options"
                    label="Escolher"                    
                    class="select"
                    @input="emits('selected', $event)"
                />
            </div>
            <div class="carousel-item-options-wrapper" v-else>
                <div
                    class="carousel-item-options-item"
                    v-for="(option, i) of options"
                    :key="i"
                    @click="emits('selected', option);"
                >
                    {{ option }}
                </div>
            </div>
        </div>
    </div>
</template>

<style lang="scss">
    .carousel-item {
        font-family: 'IBM Plex Sans';
        &-wrapper {
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            align-items: center;
            min-width: 311px;
            width: 100%;
            height: 100%;
            border: 1.5px solid #d5d5d5;
            border-radius: 20px;
            padding: 21px 24px;
        }

        &-header {
            display: flex;
            flex-direction: column;
            justify-content: flex-start;
            align-items: flex-start;
            width: 100%;

            &-icon {
                margin-bottom: 8px;
            }

            &-text {
                display: flex;
                flex-direction: column;
                justify-content: flex-start;
                align-items: flex-start;

                &-title {
                    font-size: 22px;
                    font-weight: 500;
                    line-height: 30.8px;
                    color: black;
                }   
                
                &-subtitle {
                    font-size: 16px;
                    font-weight: 400;
                    line-height: 22.4px;
                    color: black;
                }
            }
        }

        &-options {
            display: flex;
            flex-direction: column;
            justify-content: flex-end;
            align-items: flex-start;
            width: 100%;

            &-wrapper {
                display: flex;
                flex-direction: column;
                justify-content: flex-end;
                align-items: flex-start;
                width: 100%;
            }

            &-item {
                display: flex;
                justify-content: flex-start;
                align-items: center;
                width: 100%;
                height: 49px;
                font-size: 14px;
                line-height: 22.4px;
                border-radius: 10px;
                padding: 14px;
                border: 1.5px solid #d5d5d5;
                color: black;
                margin-bottom: 8px;
            }
        }
    }

    @media (min-width: 1024px) {
        .carousel-item {
            font-family: 'IBM Plex Sans';
            &-wrapper {
                display: flex;
                flex-direction: column;
                justify-content: space-between;
                align-items: center;
                min-width: 311px;
                width: 100%;
                height: 100%;
                border: 1.5px solid #d5d5d5;
                border-radius: 20px;
                padding: 21px 24px;
            }

            &-header {
                display: flex;
                flex-direction: row;
                justify-content: flex-start;
                align-items: flex-start;
                width: 100%;

                &-icon {
                    margin-bottom: 8px;
                    margin-right: 20px;
                }

                &-text {
                    display: flex;
                    flex-direction: column;
                    justify-content: flex-start;
                    align-items: flex-start;

                    &-title {
                        font-size: 18px;
                        font-weight: 500;
                        line-height: 25.2px;
                        color: black;
                    }   
                    
                    &-subtitle {
                        font-size: 14px;
                        font-weight: 400;
                        line-height: 19.6px;
                        color: black;
                    }
                }
            }

            &-options {
                display: flex;
                flex-direction: column;
                justify-content: flex-end;
                align-items: flex-start;
                width: 100%;

                &-wrapper {
                    display: flex;
                    flex-direction: column;
                    justify-content: flex-end;
                    align-items: flex-start;
                    width: 100%;
                }

                &-item {
                    display: flex;
                    justify-content: flex-start;
                    align-items: center;
                    width: 100%;
                    height: 49px;
                    font-size: 14px;
                    line-height: 22.4px;
                    border-radius: 10px;
                    padding: 14px;
                    border: 1.5px solid #d5d5d5;
                    color: black;
                    margin-bottom: 8px;
                }
            }
        }
    }
</style>