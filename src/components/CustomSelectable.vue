<template>
    <div @click="emit('click', value)" class="selectable-wrapper" :style= "[isSelected ? 'border: 1.5px solid #FC4D04;background-color: #FC4D04;' : 'border: 1.5px solid #D5D5D5']">
        <div v-if="!!icon" class="selectable-icon-wrapper">
            <p>{{ icon }}</p>
        </div>
        <div v-if="!!icon" class="selectable-description-wrapper" :style="[isSelected ? 'color: #fff' : 'color: #000']">
            <span>{{ description }}</span>
        </div>

        <div v-if="!icon" class="selectable-slot-wrapper" :style="[isSelected ? 'color: #fff' : 'color: #000']">
            <slot></slot>
        </div>
        
    </div>
</template>

<script lang="ts" setup>
    defineProps<{
        icon?: string,
        description?: string,
        isSelected: boolean,
        value: string
    }>()

    const emit = defineEmits(['click'])
</script>

<style lang="scss">
    .selectable {
        &-wrapper {
            display: flex;
            justify-content: center;
            align-items: center;
            width: 100%;
            padding: 20px 10px;
            height: auto;           
            border-radius: 20px;
            cursor: pointer;

            &:hover {
                border: 1.5px solid #FC4D04 !important;
            }
        }        

        &-icon-wrapper {
            display: flex;
            justify-content: center;
            align-items: center;
            width: 22.5%;

            p {
                font-size: 30px;
            }
        }

        &-description-wrapper {
            display: flex;
            justify-content: flex-start;
            align-items: center;
            width: 77.5%;
            font-size: 14px;
            line-height: 22.4px;
            font-weight: 500;

            span {
                max-width: 244px;
            }
        }

        &-slot-wrapper {
            display: flex;
            justify-content: flex-start;
            align-items: center;
            width: 100%;
            font-size: 14px;
            line-height: 22.4px;
            font-weight: 500;
        } 
    }

    @media (min-width: 1024px) {
        .selectable {
            &-wrapper {
                display: flex;
                flex-direction: column;
                justify-content: flex-start;
                align-items: center;
                width: 100%;
                text-align: center;
                height: 246px;           
                border-radius: 20px;
            }

            &-icon-wrapper {
                display: flex;
                justify-content: center;
                align-items: center;
                width: 100%;
                margin-top: 0px;
                margin-bottom: 15px;

                p {
                    font-size: 60px;
                }
            }

            &-description-wrapper {
                display: flex;
                justify-content: center;
                align-items: center;
                width: 100%;
                font-size: 14px;
                line-height: 22.4px;
                font-weight: 500;

                span {
                    max-width: 244px;
                    font-weight: 500;
                }
            }

            &-slot-wrapper {
                display: flex;
                justify-content: flex-start;
                align-items: center;
                width: 100%;
                font-size: 14px;
                line-height: 22.4px;
                font-weight: 500;
            } 
        }   
    }
</style>