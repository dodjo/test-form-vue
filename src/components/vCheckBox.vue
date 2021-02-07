<template>
    <div class="checkbox">
        <label>
        <div class="checkbox__input" :class="{'checkbox__input_checked':!!checked}"></div>
        <input type="checkbox" :checked="!!checked" @change="$emit('change', $event.target.checked)">
            <slot/>
        </label>
    </div>
</template>

<script>
export default {
model: {
        prop: 'checked',
        event: 'change'
    },
props: {
        checked : {
            default : false
        },
    }
}
</script>

<style lang="scss">
    .checkbox {

        input {
            position: absolute;
            z-index: -1;
            opacity: 0;
        }

        label {
            display: flex;
            align-items: center;
            flex-wrap: wrap;
            // user-select: none;
            font-family: IBM Plex Sans;
            font-style: normal;
            font-weight: 500;
            font-size: 16px;
            line-height: 21px;
            color: #756F86;
            white-space:pre-wrap;
        }

        &__input {
            display: inline-block;
            width: 28px;
            height: 28px;
            background: #FFFFFF;
            border: 1px solid #DBE2EA;
            box-sizing: border-box;
            box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04);
            border-radius: 4px;
            margin-right: 10px;
            cursor: pointer;

            &_checked {
                border: 2px solid #0880AE;
                background:  url('../assets/Check.svg');
            }
        }
    }

</style>