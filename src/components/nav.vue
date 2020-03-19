<template>
    <div class="navbar">
        <div class="logo"><a href="#"><img class="img-fill" src="../assets/logo.png" alt="logo"></a></div>
        <div class="menu-bar" @click="isShowNavList = !isShowNavList">
            <span></span>
            <span></span>
            <span></span>
        </div>
        <div v-if="isShowNavList" class="nav-list">
            <ul class="nav">
                <li v-for="(item, idx) in navList" :key="idx" :class="getActiveClass(idx)" @click.prevent="jumpToPage(idx)"><a href="#">{{ item }}</a></li>
                <!-- <li><a href="#">Services</a></li>
                <li><a href="#">Histroy</a></li>
                <li><a href="#">Actions</a></li> -->
            </ul>
        </div>
        <div class="search">
            <span class="icon-search"></span>
            <form action="#" method="GET">
                <input class="ipt-search" type="search" placeholder="search..." v-model="keyWord">
                <button class="btn-serach" @click.prevent="startSearch"></button>
            </form>
        </div>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class Nav extends Vue {
    private keyWord = '';
    private isShowNavList = false;
    private navList = ['Home', 'Services', 'Histroy', 'Actions'];
    private activeIdx = 0;
    
    private startSearch() {
        console.log('开始搜索关键词：' + this.keyWord)
    } 
    private jumpToPage(i: number) {
        this.activeIdx = i;
        if (document.documentElement.clientWidth <= 910) {
            this.isShowNavList = false;
        }
    }
    private getActiveClass(i: number) {
        let className = '';
        if(this.activeIdx === i) {
            className = 'active';
        }
        return className;
    }
    initNav() {
        if (document.documentElement.clientWidth > 910) {
            this.isShowNavList = true;
        } else {
            this.isShowNavList = false;
        }
    }
    mounted() {
        window.addEventListener('resize', this.initNav.bind(this))
    }

}
</script>

<style lang="less" scoped>
@import '../assets/var';
.navbar {
    display: flex;
    justify-content: space-between;
    align-items: baseline;
    margin-bottom: 20px;
    position: relative;
    .logo {
        width: 48px;
        height: 43px;
        flex: none;
    }
    .nav-list {
        background: #fff;
        border-radius: 6px;
        .nav {
            display: flex;
            font-size: 16px;
            > li {
                transition: all ease-in .2s .2s;
                line-height: 42px;
                height: 42px;
                padding: 0 23px;
                > a {
                    color: #666977;
                }
                &.active {
                    > a {
                        color: #14233c;
                        font-weight: bold;
                    }
                }
            }
        }
    }
        
    .search {
        transition: all ease-in .2s .2s;
        position: relative;
        height: 42px;
        width: 270px;
        border-radius: 21px;
        overflow: hidden;
        position: relative;
        .icon-search {
            width: 24px;
            height: 24px;
            background: url(../assets/search.png) center no-repeat;
        }
        form {
            display: block;
            width: 100%;
        }
        .ipt-search {
            height: 42px;
            line-height: 42px;
            font-size: 14px;
            width: 100%;
            background: #f8f8f8;
            border: none;
            padding: 0 45px 0 22px;
            outline: none;
        }
        .btn-serach {
            border: none;
            background: transparent;
            width: 24px;
            height: 24px;
            background: url(../assets/search.png) center no-repeat;
            position: absolute;
            right: 20px;
            top: 50%;
            margin-top: -12px;
            outline: none;
            cursor: pointer;
        }
    }
    .menu-bar {
        display: none;
        width: 48px;
        height: 48px;
        cursor: pointer;
        background: #fff;
        box-sizing: border-box;
        padding-top: 8px;
        border-radius: 6px;
        > span {
            display: block;
            height: 3px;
            border-radius: 2px;
            width: 58%;
            margin: 6px auto;
            background: #a7a9b1;
        }
        &:hover {
            background: #f1f1f1;
        }
    }
    @media (max-width: @lgScreen) {
        transition: width ease-in .2s .2s;
        .nav-list .nav > li {
            transition: all ease-in .2s .2s;
            padding: 0 12px;
        }
        .search {
            transition: all ease-in .2s .2s;
            width: 200px;
        }
    }
    @media (max-width: @mdScreen) {
        .search {
            // width: 32px;
            // height: 32px;
            display: none;
        }
    }
    @media (max-width: @smScreen) {
    .nav-list {
        // display: none;
        position: absolute;
        z-index: 5;
        top: 48px;
        right: 0;
        width:200px;
        box-shadow: 0 10px 20px rgba(0, 0, 0, .2);
        > .nav {
            flex-wrap: wrap;
            > li {
                width: 100%;
                box-sizing: border-box;
                flex: none;
                line-height: 50px;
                height: 50px;
                &:hover, &:active {
                    background: #eee;
                }
            }
            
        }
    }
    // .search {
    //     display: none;
    //     .icon-search {
    //         display: block;
    //     }
    //     form {
    //         display: none;
    //     }
        
    // }
    .menu-bar {
        display: block;
    }
  }
}
</style>