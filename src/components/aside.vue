<template>
    <div class="aside">
        <div class="user">
            <div class="user-notice new">
                <i class="icon-notice"></i>
            </div>
            <div class="user-head">
                <span class="name">UserName</span>
                <span class="head"><img class="img-fill" src="../assets/head.jpg" alt="头像"></span>
            </div>
        </div>
        <div class="balance">
            <VeRing :data="chartData" height="300px" :legend-visible="false" :settings="chartSettings" />
        </div>
        <div class="transactions">
            <div class="title">
                <h3>Transactions</h3>
                <div class="date">
                    <span @click="isShowDateList = !isShowDateList">{{ selectDate }}</span>
                    <div v-if="isShowDateList" class="selectdate">
                        <ul>
                            <li v-for="(item, idx) in dateList" :key="idx" @click="select(idx)">{{ item }}</li>
                        </ul>
                    </div>
                </div>
            </div>
            <div class="tran-list">
                <ul>
                    <li>
                        <i class="icon"><img class="img-fill" src="../assets/international.png" alt=""></i>
                        <p>Type checking in progress</p>
                        <span class="red">-$100</span>
                    </li>
                    <li>
                        <i class="icon"><img class="img-fill" src="../assets/international.png" alt=""></i>
                        <p>Type checking in progress</p>
                        <span class="green">+$100</span>
                    </li>
                    <li>
                        <i class="icon"><img class="img-fill" src="../assets/international.png" alt=""></i>
                        <p>Type checking in progress</p>
                        <span class="green">+$100</span>
                    </li>
                </ul>
            </div>
        </div>
        <div class="transfer">
            <a href="#" class="btn">
                <span>Transfer Money</span>
                <span>→</span>
            </a>
        </div>
        <div class="msg">
            <i class="icon-message"></i>
        </div>
    </div>
</template>

<script>
import VeRing from 'v-charts/lib/ring.common'


export default {
    name: 'Aside',
    data() {
        return {
            chartSettings: {
                offsetY: 150
            },
            dateList: ['Today', 'Monday', 'Tuesday'],
            isShowDateList: false,
            selectDate: '',
            chartData: {
                columns: ['日期', '访问用户'],
                rows: [
                    { '日期': '1/1', '访问用户': 1393 },
                    { '日期': '1/2', '访问用户': 3530 },
                    { '日期': '1/3', '访问用户': 2923 },
                    { '日期': '1/4', '访问用户': 1723 },
                    { '日期': '1/5', '访问用户': 3792 },
                    { '日期': '1/6', '访问用户': 4593 }
                ]
            }
        }
    },
    components: {
        VeRing
    },
    methods: {
        select(i) {
            this.selectDate = this.dateList[i];
            this.isShowDateList = false;
        }
    },
    mounted() {
        this.selectDate = this.dateList[0]
    }
}
</script>

<style lang="less" scoped>
@import '../assets/var';

.aside {
    background: #fff;
    border-radius: 50px;
    box-shadow: -20px 0 50px rgba(97, 97, 97, 0.1);
    flex: none;
    width: 380px;
    transition: width ease-in .2s;
    @media (max-width: @lgScreen) {
        width: 320px;
        transition: width ease-in .2s;
    }
    @media (max-width: @mdScreen) {
        width: 260px;
        transition: width ease-in .2s;
        .transactions {
            .tran-list {
                > ul > li > i.icon {
                    display: none;
                }
            }
        }
    }
    @media (max-width: @smScreen) {
        width: 0px;
        overflow: hidden;
    
    }
}
.user {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 40px 0;
    margin: 0 34px;
    .user-notice {
        flex: none;
        width: 32px;
        height: 32px;
        position: relative;
        .icon-notice {
            width: 32px;
            height: 32px;
            display: block;
            background: url(../assets/notification.png) no-repeat center;
            cursor: pointer;
            background-size: contain;
        }
        &.new::after {
            content: '\20';
            width: 8px;
            height: 8px;
            background: @redColor;
            position: absolute;
            right: 3px;
            top: 3px;
            border-radius: 50%;
        }
    }
    
    .user-head {
        display: flex;
        align-items: center;
        .name {
            color: #223048;
            font-size: 14px;
            display: block;
            height: 48px;
            line-height: 48px;
            overflow: hidden;
            text-overflow: ellipsis;
            white-space: nowrap;
            max-width: 120px;
            margin-right: 15px;
            font-weight: bold;
        }
        .head {
            width: 48px;
            height: 48px;
            border-radius: 50%;
            border: 1px solid #eee;
            display: block;
            overflow: hidden;
        }
    }
}
.balance {
    height: 300px;
}
.transactions {
    padding: 0 28px;
    .title {
        color: #a7a9b1;
        font-size: 16px;
        display: flex;
        justify-content: space-between;
        line-height: 40px;
        height: 40px;
        h3 {
            font-size: 16px;
            font-weight: 500;
            line-height: 40px;
        }
        .date {
            position: relative;
            > span {
                cursor: pointer;
                &::after {
                    content: '>';
                    transform: rotate(90deg);
                    margin-left: 6px;
                    display: inline-block;
                }
            }
            .selectdate {
                // display: block;
                width: 110px;
                background: #fff;
                box-shadow: 0 10px 15px rgba(100, 100, 100, .3);
                border-radius: 10px;
                position: absolute;
                right: -20px;
                li {
                    line-height: 36px;
                    height: 36px;
                    cursor: pointer;
                    padding: 0 10px;
                    text-align: left;
                    &:hover {
                        background: #eee;
                    } 
                }
            }
        }
    }

    .tran-list {
        > ul > li {
            display: flex;
            align-items: center;
            height: 75px;
            font-size: 16px;
            font-weight: 600;
            > i.icon {
                flex: none;
                display: block;
                background-color: #fff;
                border-radius: 12px;
                margin-right: 20px;
                width: 60px;
                height: 60px;
                box-sizing: border-box;
                padding: 8px;
                box-shadow: 0 0 16px rgba(115, 115, 115, 0.1);
            }
            > p {
                flex: auto;
                overflow: hidden;
                text-overflow: ellipsis;
                white-space: nowrap;
                width: 100%;
            }
            > span {
                margin-left: 20px;
                display: inline-block;
                flex: none;
                &.red {
                    color: @redColor;
                }
                &.green {
                    color: @greenColor;
                }
            }
        }
    }
}
.transfer {
    margin: 40px 35px;
    a, a:link, a:visited, a:hover {
        color: #fff;
    }
    .btn {
        display: flex;
        align-items: center;
        padding: 0 28px;
        background: @redColor;
        height: 54px;
        border-radius: 27px;
        justify-content: space-between;
        box-shadow: 0 15x 20px rgba(255, 77, 86, .3);
        &:hover {
            opacity: .85;
        }
    }
}
.msg {
    margin: 0 35px;
    padding: 20px 0 30px;
    text-align: right;
    .icon-message {
        display: inline-block;
        height: 54px;
        width: 54px;
        border-radius: 50%;
        overflow: hidden;
        background: @greenColor;
        position: relative;
        box-shadow: 0 15px 20px rgba(14, 128, 154, .2);
        cursor: pointer;
        &::after {
            content: '\20';
            width: 100%;
            height: 100%;
            position: absolute;
            top: 0;
            left: 0;
            background: url(../assets/message.png) center no-repeat;
        }
        &:hover {
            opacity: .85;
        }
    }
}
</style>