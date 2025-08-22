<template>
    <img src="@/assets/menu/1.png" class="bg">
    <div class="rel pl30 pr30 pt80">

        <div class="tc">
            <div class="linearTxt size80 bold">LP持仓入单</div>
        </div>
        
        <div class="top mt60">
            <div class="flex jb ac">
                <div class="flex ac">
                    <div class="line mr10"></div>
                    <div class="size24 bold">入单金额</div>
                </div>
                <div class="flex ac">
                    <img src="@/assets/usdt.png" class="img40 mr10">
                    <div class="size20 bold">USDT</div>
                </div>
            </div>
            <div class="flex jb mt35">
                <div class="numItem" :class="amount==item?'numAct':'numDef'" v-for="(item,index) in nums" :key="index" @click="amount=item">{{ item }}</div>
            </div>
            <div class="amountBox mt60 flex ac">
                <img src="@/assets/menu/sub.png" class="img48" @click="sub">
                <input type="number" v-model="amount" class="flex1 size40 bold tc">
                <img src="@/assets/menu/add.png" class="img48" @click="add">
            </div>
            <div class="btn mt60">确认入单</div>
        </div>
        <div class="box mt60">
            <div class="flex jb">
                <div>
                    <div class="size24">待领取收益(EA)</div>
                    <div class="linearTxt size40 bold mt10">1000</div>
                </div>
                <div class="btn">领取</div>
            </div>
        </div>
        <div class="flex jb mt60 mb40">
            <div class="tab" :class="current==0?'tabAct':'tabDef'" @click="tabsClick(0)">进行中</div>
            <div class="tab" :class="current==1?'tabAct':'tabDef'" @click="tabsClick(1)">已完成</div>
        </div>
        <div class="rel">
            <div class="mask"></div>
            <div class="scroll">
                <div class="card" :class="index<list.length-1?'mb30':''" v-for="(item,index) in list" :key="index">
                    <div class="flex jb ac">
                        <div class="opc5 size24">入单金额</div>
                        <!-- <div class="cardBtn">赎回</div> -->
                        <div class="size24 opc5 done">已完成</div>
                    </div>
                    <div class="flex ac mt10">
                        <img src="@/assets/usdt.png" class="img40 mr12">
                        <div class="size40 bold">100</div>
                    </div>
                    <div class="flex jb ac mt40">
                        <div class="opc5 size24">累计收益(EA)</div>
                        <div class="linearTxt size32 bold">1000</div>
                    </div>
                </div>
            </div>
        </div>
        <div class="bot rel">
            <img src="@/assets/usdt.png" class="vip">
            <div class="flex jc ac">
                <img src="@/assets/menu/4.png" class="pic4">
                <div class="ml30 mr30 linearTxt size32 bold">团队</div>
                <img src="@/assets/menu/5.png" class="pic4">
            </div>
            <div class="tc mt60">
                <div class="linearTxt size60 bold">10000</div>
                <div class="size24 opc5 mt20">团队总业绩(USDT)</div>
            </div>
            <div class="level mt86 flex ac">当前等级: V3</div>
        </div>
    </div>

    <van-popup v-model:show="show" style="background-color: transparent !important;">
        <div class="pop">
            <div class="title flex jb ac">
                <div class="size28 bold">入单</div>
                <div class="opc6">
                    <van-icon name="cross" :size="25" />
                </div>
            </div>
            <div class="content">
                <div class="size28 bold">
                    <span>确认入单</span>
                    <span class="main ml10 mr10 size48">100</span>
                    <span class="main">usdt</span>
                </div>
                <div class="popbtn mt50">确认入单</div>
            </div>
        </div>
    </van-popup>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const nums = [10, 50, 100, 300, 500]
const amount = ref(10)
const sub = () => {
    if(amount.value<=1)return amount.value=1
    else amount.value -= 1
}
const add = () => amount.value += 1

const current = ref(0)
const tabsClick = (index:number) => {
    if(current.value==index)return
    current.value = index
}

const list = [1,1,1,1,1]

const show = ref(false)
</script>

<style lang="scss" scoped>
.bg{
    width: 750px;
    height: 750px;
    position: absolute;
    top: 100px;
}
.top{
    width: 100%;
    height: 584px;
    background-image: url("@/assets/menu/2.png");
    background-size: 100% 100%;
    padding: 85px 30px 0 30px;
    .line{
        width: 4px;
        height: 20px;
        background-color: $main-color;
    }
    .numItem{
        width: 116px;
        height: 68px;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 24px;
        font-weight: bold;
    }
    .numDef{
        background-color: #000000;
        border: 1px solid #FFFFFF;
    }
    .numAct{
        @include linear;
        color: #000000;
    }
    .amountBox{
        background-color: #1A1A1A;
        height: 88px;
        padding: 0 20px;
    }
    .btn{
        @include linear(1);
        height: 88px;
        line-height: 88px;
        text-align: center;
        color: #000000;
        font-size: 26px;
        font-weight: bold;
    }
}
.box{
    height: 175px;
    background-image: url("@/assets/menu/3.png");
    background-size: 100% 100%;
    padding: 40px 30px 0 30px;
    .btn{
        min-width: 160px;
        padding: 0 30px;
        background-color: #FFFFFF;
        color: #000000;
        height: 56px;
        line-height: 56px;
        font-size: 24px;
        text-align: center;
    }
}
.tab{
    width: 335px;
    height: 68px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 28px;
    font-weight: bold;
}
.tabAct{
    @include linear;
    color: #000000;
}
.tabDef{
    border: 2px solid #FFFFFF80;
    color: #FFFFFF80;
}
.scroll{
    width: 100%;
    height: 846px;
    overflow-y: scroll;
    &::-webkit-scrollbar{
        display: none;
    }
    .card{
        width: 100%;
        height: 262px;
        background-color: #1A1A1A;
        padding: 30px 30px 0 30px;
        .cardBtn{
            @include linear(1);
            min-width: 88px;
            height: 50px;
            text-align: center;
            line-height: 50px;
            font-size: 24px;
            padding: 0 20px;
            color: #000000;
        }
        .done{
            height: 50px;
            line-height: 50px; 
        }
    }
}
.mask{
    width: 100%;
    height: 262px;
    background: linear-gradient(#00000000, #000000);
    position: absolute;
    bottom: 0;
    left: 0;
    z-index: 1;
}
.bot{
    padding: 80px 0 100px 0;
    background-color: #000000;
    .pic4{
        width: 190px;
        height: 30px;
    }
    .level{
        height: 94px;
        border: 1px solid $main-color;
        color: $main-color;
        padding: 0 30px;
        font-size: 28px;
        font-weight: bold;
    }
    .vip{
        width: 120px;
        height: 120px;
        position: absolute;
        right: 30px;
        bottom: 120px; 
        z-index: 1;
    }
}
.pop{
    width: 590px;
    border: 1px solid $main-color;
    .title{
        height: 88px;
        padding: 0 30px;
        background-color: $main-color;
        color: #000000;
    }
    .content{
        padding: 50px 30px 60px 30px;
        background-color: #1A1A1A;
        .popbtn{
            @include linear;
            height: 68px;
            line-height: 68px;
            text-align: center;
            color: #000000;
            font-weight: bold;
            font-size: 26px;
        }
    }
}
</style>