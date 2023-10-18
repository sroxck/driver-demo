<!--
 * @Author: sroxck
 * @Date: 2023-10-18 09:53:04
 * @LastEditors: sroxck
 * @LastEditTime: 2023-10-18 10:55:22
 * @Description: 
-->
# driver demo

use driver.js to complete the boot page

1. install driver.js and import it and style
``` ts
// pnpm install driver.js
import {driver} from './driver.js';
import 'driver.js/dist/driver.css';

```
2. call driver function with config object
``` ts
const driverObj = driver({
  allowClose: false, // whether to display close button  
  popoverClass: 'driverjs-theme',// specify class to dialog style 
  showProgress: false, // whether to display current step 
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
```
3. start up drive
   
``` ts
driverObj.drive() // 可以传参,值为步骤
```
