<template>
    <button class="v-btn">
        <slot></slot>
    </button>
</template>

<script>
export default {

}
</script>

<style lang="scss">
    .v-btn {
        width: 100%;
        height: 56px;
        padding: 18px 65px;
        color: #EBF4F8;
        background: #0880AE;
        box-shadow: 0px 2px 4px rgba(44, 39, 56, 0.08), 0px 4px 8px rgba(44, 39, 56, 0.08);
        border-radius: 6px;
        border:none;

        font-family: IBM Plex Sans;
        font-style: normal;
        font-weight: 500;
        font-size: 16px;
        line-height: 21px;
        text-align: center;
        outline: none;
        cursor: pointer;

        &:hover:enabled {
            box-shadow: 0px 12px 24px rgba(44, 39, 56, 0.08), 0px 24px 48px rgba(44, 39, 56, 0.16);
        }

        &:active {
            border: 2px solid rgba(44, 39, 56, 0.86);
        }

        &:disabled {
            background: #DBE2EA;
            color: #B1B5BF;
        }
    }
</style>