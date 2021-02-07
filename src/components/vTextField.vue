<template>
    <div class="text-field">
        <label for="field">{{label}}</label>
        <input type="text" :placeholder="placeholder" id="field" :value="value" @input="$emit('input',$event.target.value)" autocomplete="off">
        <div class="validation-message">{{message}}</div>
    </div>
</template>

<script>
export default {
    props: {
        label: {
            type: String,
            default: 'Label'
        },
        value : {
            default: ''
        },
        placeholder: {
            type: String,
            default: 'Placeholder'
        },
        message : {
            default: ''
        }
    }

}
</script>

<style lang="scss">
    .text-field {
        font-family: IBM Plex Sans;
        font-style: normal;
        font-weight: 500;
        font-size: 16px;
        line-height: 21px;

        label {
            padding-bottom: 7px;
            display: block;
            color: #756F86;
        }

        input {
            font-family: IBM Plex Sans;
            font-style: normal;
            font-weight: 400;
            font-size: 16px;
            line-height: 21px;

            height: 52px;
            width: 100%;
            box-sizing: border-box;
            padding: 16px;
            background: #FFFFFF;
            border: 1px solid #DBE2EA;
            box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04);
            border-radius: 6px;
            outline: none;
            color: #2C2738;

            &::placeholder{
                color: #7C9CBF;
            }

            &:focus {
                border: 2px solid #0880AE;
            }
        }

        .validation-message {
            height: 18px;
            padding-top: 8px;
            font-size: 14px;
            line-height: 18px;
            color: #FF7171;
        }
    }

</style>