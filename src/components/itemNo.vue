<script setup></script>

<template>
  <div class="no">
    <div class="no-hd">
      <ul>
        <li>321123</li>
        <li>123321</li>
      </ul>
    </div>
    <div class="no-bd">
      <ul>
        <li>需求人数</li>
        <li>供应人数</li>
      </ul>
    </div>
  </div>
</template>

<style lang="less" scoped>
li {
  list-style: none;
}

// 声明字体
@font-face {
  font-family: electronicFont;
  src: url(@/font/DS-DIGIT.TTF);
}
.no {
  background-color: rgba(101, 132, 226, 0.1);
  padding: 0.75vw;

  .no-hd {
    position: relative;
    border: 1px solid rgba(25, 186, 139, 0.17);

    &::before {
      position: absolute;
      top: 0;
      left: 0;
      content: '';
      width: 30px;
      height: 10px;
      border-top: 2px solid #02a6b5;
      border-left: 2px solid #02a6b5;
    }

    &::after {
      position: absolute;
      bottom: 0;
      right: 0;
      content: '';
      width: 30px;
      height: 10px;
      border-bottom: 2px solid #02a6b5;
      border-right: 2px solid #02a6b5;
    }

    ul {
      display: flex;

      li {
        position: relative;
        flex: 1;
        line-height: 4vw;
        font-size: 3.5vw;
        color: #ffeb7b;
        text-align: center;
        font-family: 'electronicFont';

        &::after {
          content: '';
          position: absolute;
          top: 25%;
          right: 0;
          height: 50%;
          width: 1px;
          background: rgba(255, 255, 255, 0.2);
        }
      }
    }
  }

  .no-bd {
    ul {
      display: flex;

      li {
        flex: 1;
        text-align: center;
        color: rgba(255, 255, 255, 0.7);
        font-size: 0.9vw;
        height: 2vw;
        line-height: 2vw;
        padding-top: 0.5vw;
      }
    }
  }
}
</style>
