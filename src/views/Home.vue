<template>
  <div class="home">
    <div class="cards">
      <div class="home-title">
        <h2>Cards</h2>
        <a class="more" href="#">View all cards</a>
      </div>
      <div class="card-list">
        <div class="card-item red">
          <div class="balance">
            <p>Test balance</p>
            <h4>$88,888</h4>
          </div>
          <p class="number">**** **** **** **88</p>
          <p class="monzo">Mobzo</p>
        </div>
        <div class="card-item green">

        </div>
        <div class="add-new">
          <i class="icon-add">+</i>
          <p>Add New Card</p>
        </div>
      </div>
    </div>
    <div class="home-main">
      <div class="services">
        <div class="home-title">
          <h2>Main Services</h2>
          <a class="more" href="#">View all</a>
        </div>
        <div class="services-list">
          <div class="item">
            <i class="icon"><img src="../assets/international.png" alt="服务图标"></i>
            <p>Trasactions</p>
          </div>
          <div class="item">
            <i class="icon"><img src="../assets/international.png" alt="服务图标"></i>
            <p>Trasactions</p>
          </div>
          <div class="item">
            <i class="icon"><img src="../assets/international.png" alt="服务图标"></i>
            <p>Trasactions</p>
          </div>
          <div class="item">
            <i class="icon"><img src="../assets/international.png" alt="服务图标"></i>
            <p>Trasactions</p>
          </div>
          <div class="item">
            <i class="icon"><img src="../assets/international.png" alt="服务图标"></i>
            <p>Trasactions</p>
          </div>
          <div class="item">
            <i class="icon"><img src="../assets/international.png" alt="服务图标"></i>
            <p>Trasactions</p>
          </div>
        </div>
      </div>
      <div class="main-right">
        <div class="current">
          <div class="home-title">
            <h2>Current</h2>
            <a class="more" href="#">View all</a>
          </div>
          <div class="current-con">
            <ul>
              <li>
                <span class="number">123456789</span>
                <span class="line"></span>
                <span class="balance">$88,888</span>
              </li>
              <li>
                <span class="number">123456789</span>
                <span class="line"></span>
                <span class="balance">$8,888,888</span>
              </li>
              <li>
                <span class="number">123456789</span>
                <span class="line"></span>
                <span class="balance">$88,888</span>
              </li>
            </ul>
          </div>
        </div>
        <div class="savings">
          <div class="home-title">
            <h2>Savings</h2>
            <a class="more" href="#">View all</a>
          </div>
          <div class="chart">
            <VeLine :data="chartData" :grid="grid" height="200px" :legend-visible="false" :yAxis="yAxis" />
          </div>
        </div>
      </div>
      
    </div>
    
  </div>
</template>

<script>
// @ is an alias to /src
import VeLine from 'v-charts/lib/line.common';
export default {
  name: 'Home',
  components: {
    VeLine
  },
  data() {
    return {
      grid: {
        top: '10%',
        left: '5%',
        right: '5%',
        bottom: '10%'
      },
      yAxis: {
        splitNumber: 2,
      },
      chartData: {
        columns: ['date', 'PV'],
        rows: [
          { 'date': '01-01', 'PV': 20 },
          { 'date': '01-02', 'PV': 40 },
          { 'date': '01-03', 'PV': 50 },
          { 'date': '01-04', 'PV': 35 },
          { 'date': '01-05', 'PV': 65 },
          { 'date': '01-06', 'PV': 72 }
        ]
      }
    }
  }
}
</script>
<style lang="less" scoped>
@import '../assets/var';

.home {
  .home-title {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 45px 0 25px;
    h2 {
      font-weight: 500;
      font-size: 20px;
      margin: 0;
    }
    .more {
      color: #a7a9b1;
      font-size: 13px;
    }
  }
  .cards {
    .card-list {
      display: flex;
      .card-item {
        border-radius: 16px;
        width: 302px;
        height: 174px;
        margin-right: 18px;
        text-align: left;
        position: relative;
        box-sizing: border-box;
        padding: 22px 28px 0;
        letter-spacing: 1px;
        // margin-bottom: 20px;
        &.red {
          background: @redColor;
          color: darken(@redColor, 30%);
        }
        &.green {
          background: @greenColor;
          color: darken(@greenColor, 30%);
        }
        .balance {
          > p {
            font-size: 12px;
            line-height: 1.5;
          }
          > h4 {
            font-size: 16px;
            color: #fff;
            font-weight: 500;
            line-height: 1.5;
          }
        }
        .number {
          padding-top: 30px;
          padding-bottom: 20px;
          font-size: 18px;
          font-weight: bold;
          white-space: nowrap;
        }
        .monzo {
          font-size: 18px;
          color: #fff;
          font-weight: 400;
        }
        &::after {
          content: '\20';
          display: block;
          position: absolute;
          bottom: 16px;
          right: 20px;
          width: 33px;
          height: 33px;
          border-radius: 50%;
          background: @yellowColor;
          box-shadow: -20px 0 0 rgba(201, 1, 17, .8);
        }
      }
      .add-new {
        background: #f8f8f8;
        border-radius: 16px;
        // margin-bottom: 20px;
        max-width: 260px;
        flex: auto;
        .icon-add {
          font-size: 30px;
          color: #d7d7d7;
          border: 1px dashed #d7d7d7;
          width: 43px;
          height: 43px;
          border-radius: 50%;
          text-align: center;
          line-height: 43px;
          display: block;
          margin: 56px auto 0;
        }
        > p {
          color: #d7d7d7;
          font-size: 14px;
          line-height: 1.5;
          padding-top: 6px;
          text-align: center;
        }
      }
    }
  }
  .home-main {
    display: flex;
    .services {
      width: 256px;
      flex: none;
      margin-right: 65px;
      transition: all ease-in .2s .2s;
      .services-list {
        display: flex;
        flex-wrap: wrap;
        margin-right: -18px;
        .item {
          transition: all ease-in .2s .2s;
          flex: none;
          width: 119px;
          height: 119px;
          background: #fff;
          box-shadow: 0 0 20px rgba(105, 105, 105, .2);
          margin-right: 18px;
          margin-bottom: 20px;
          border-radius: 16px;
          .icon {
            width: 36px;
            height: 36px;
            display: block;
            margin: 30px auto 0;
            > img {
              display: block;
              width: 100%;
            }
          }
          > p {
            font-size: 12px;
            line-height: 2;
            color: #14233c;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
          }
        }
      }
    }
    .main-right {
      flex: auto;
      .current {
        .current-con {
          > ul > li {
            display: flex;
            font-size: 16px;
            align-items: center;
            height: 38px;
            line-height: 38px;
            .number {
              flex: none;
              color: #a7a9b1;
              white-space: nowrap;
              overflow: hidden;
            }
            .line {
              width: 100%;
              flex: auto;
              margin: 0 20px;
              border-bottom: 1px dashed #e1ebe8;
            }
            .balance {
              flex: none;
              white-space: nowrap;
            }
          }
        }
      }
      .savings {
        .chart {
          height: 200px;
          width: 100%;
          // background: #eee;
        }
      }
    }
  }
  @media (max-width: @lgScreen) {
    .cards .card-list .card-item {
      transition: all ease-in .2s .2s;
      width: 260px;
    }
  }
  @media (max-width: @mdScreen) {
    .cards {
      .card-list {
        .card-item:nth-child(2) {
          display: none;
        }
      }
    }
    .home-main {
      flex-wrap: wrap;
      .services {
        transition: all ease-in .2s .2s;
        width: 100%;
        .services-list .item {
          transition: all ease-in .2s .2s;
          width: 90px;
          height: 90px;
          .icon {
            margin-top: 18px;
          }
        }
      }
    }
    
  }
  @media (max-width: @xsScreen) {
    .cards {
      .card-list {
        .card-item {
          padding: 22px 18px 0;
        }
      }
    }
  }
  .home-main {
      .services {
        .services-list .item {
          transition: all ease-in .2s .2s;
          width: 86px;
          height: 86px;
          margin-right: 16px;
          .icon {
            margin-top: 15x;
          }
        }
      }
    }
}
</style>
