<template>
    <div class="dropdown">
        <label>{{label}}</label>
        <div class="dropdown__selected" @click="showOptions = !showOptions">
            {{selected.value}}
            <i class="dropdown__icon" :class="{'dropdown__icon_down':showOptions}"></i>
        </div>
        <div class="dropdown__options" v-show="showOptions">
            <div class="dropdown__item"
            v-for="option in options"
            :key="option.id"
            @click="selectOption(option)">
                {{option.value}}
            </div>
        </div>
    </div>
</template>

<script>
export default {
    model: {
        prop: 'selected',
        event: 'select'
    },
    props: {
        label: {
            type: String,
            default: 'Label'
        },
        options: {
            type: Array,
            default () {
                return []
            }
        },
        selected:  {
            type:Object,
            default () {
                return {}
            }
        }

    },

    data() {
        return {
            showOptions: false,
        }
    },

    methods:{
        selectOption (option) {
            this.$emit('select', option)
            // this.selected = option
            this.showOptions = false
        }
    }
}
</script>

<style lang="scss">
    .dropdown{
        font-family: IBM Plex Sans;
        font-style: normal;
        font-weight: 500;
        font-size: 16px;
        line-height: 21px;
        position: relative;

        label {
            padding-bottom: 7px;
            display: block;
            color: #756F86;
        }

        &__selected {
            display: flex;
            justify-content: space-between;
            align-items: center;
            width: 100%;
            padding: 11px 11px 11px 16px;
            background: #FFFFFF;
            border: 1px solid #DBE2EA;
            box-sizing: border-box;
            box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04);
            border-radius: 6px;
            outline: none;
            appearance: none;
            cursor: pointer;
        }

        &__icon {
            display: inline-block;
            width: 28px;
            height: 28px;
            background: url('../assets/Chevron_Bottom.svg');
            transition: transform 0.2s ease;
            &_down {
                transform: rotate(180deg);
            }
        }

        &__options {
            position: absolute;
            margin-top: 4px;
            width: 100%;
            background: #FFFFFF;
            border: 1px solid #DBE2EA;
            box-sizing: border-box;
            box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04), 0px 20px 20px rgba(44, 39, 56, 0.04);
            border-radius: 6px;
            padding: 12px 0;
            user-select: none;
            z-index: 9999;
        }

        &__item {
            padding: 12px 15px;
            color: #756F86;
            &:hover {
                background: #EBF4F8;
            }
        }

    }

</style>