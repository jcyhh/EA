<template>
    <img src="@/assets/menu/1.png" class="bg">
    <div class="pt80 pl30 pr30">

        <div class="flex jc">
            <div class="">usdt余额：{{ balance }}</div>
            <div class="">币余额：{{ tokenBalance }}</div>
        </div>
        

    </div>
</template>

<script setup lang="ts">
import { useErc20 } from '@/dapp/contract/erc20/useErc20';

const { balance } = useErc20()

const { balance:tokenBalance } = useErc20(import.meta.env.VITE_MOSE)

</script>

<style lang="scss" scoped>
.bg{
    width: 750px;
    height: 750px;
}
</style>