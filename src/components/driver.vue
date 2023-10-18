<!--
 * @Author: sroxck
 * @Date: 2023-10-18 09:53:04
 * @LastEditors: sroxck
 * @LastEditTime: 2023-10-18 10:11:16
 * @Description: driver 引导页demo
-->
<script setup lang="ts">
import { driver } from 'driver.js'
import 'driver.js/dist/driver.css';

const driverObj = driver({
  allowClose: false, // 是否显示关闭按钮
  popoverClass: 'driverjs-theme',// 指定css 可以自己修改引导页的样式
  showProgress: false, // 是否显示当前是第几步
  steps: [
    { element: '.ces1', popover: { title: '标题1', description: '这是第一步', side: "right", align: 'start' } },// side控制弹窗的方向 align对齐方式
    { element: '.ces2', popover: { title: '标题2', description: '这是第二步', side: "left", align: 'start' } },
    { element: '.ces3', popover: { title: '标题3', description: '这是第三步', side: "right", align: 'start' } },
  ],
  onPopoverRender: (popover, { config, state }) => {
    console.log(config, state,'配置对象')
    // 在这个事件中可以修改引导页的样式和添加按钮 通过原生js
    const firstButton = document.createElement("button");
    firstButton.innerText = "Go to First";
    popover.footerButtons.appendChild(firstButton);
    // 点击后回到第一步
    firstButton.addEventListener("click", () => {
      driverObj.drive(0);
    });
  },
});


const start = () => driverObj.drive()
</script>

<template>
  <button @click="start">开启引导</button>
  <div>
    <div class="ces1">测试1</div>
    <div class="ces2">测试2</div>
    <div class="ces3">测试3</div>
  </div>
</template>

<style >
.driver-popover.driverjs-theme {
  background-color: #fde047;
  color: #000;
}

.driver-popover.driverjs-theme .driver-popover-title {
  font-size: 20px;
}

.driver-popover.driverjs-theme .driver-popover-title,
.driver-popover.driverjs-theme .driver-popover-description,
.driver-popover.driverjs-theme .driver-popover-progress-text {
  color: #000;
}

.driver-popover.driverjs-theme button {
  text-align: center;
  background-color: #000;
  color: #ffffff;
  border: 2px solid #000;
  text-shadow: none;
  font-size: 14px;
  border-radius: 6px;
}

.driver-popover.driverjs-theme button:hover {
  background-color: #000;
  color: #ffffff;
}

.driver-popover.driverjs-theme .driver-popover-arrow-side-left.driver-popover-arrow {
  border-left-color: #fde047;
}

.driver-popover.driverjs-theme .driver-popover-arrow-side-right.driver-popover-arrow {
  border-right-color: #fde047;
}

.driver-popover.driverjs-theme .driver-popover-arrow-side-top.driver-popover-arrow {
  border-top-color: #fde047;
}

.driver-popover.driverjs-theme .driver-popover-arrow-side-bottom.driver-popover-arrow {
  border-bottom-color: #fde047;
}


.read-the-docs {
  color: #888;
}

.ces1,
.ces2,
.ces3 {
  width: 900px;
  height: 300px
}
</style>
