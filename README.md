Power-Mall 前端页面

基于 原生 HTML/CSS/JavaScript + AJAX 实现的电商前端系统，与 [Power-Mall 后端](https://github.com/xiaoxiaojuzuicai/power-mall) 对接，完成商品浏览、购物车管理、订单提交等核心交互流程。  
开发周期：2024.04 – 2025.07 | 个人实践 · 持续优化

项目目标
- 实践前后端分离开发模式，通过 AJAX 调用 RESTful API；
- 掌握原生 JavaScript 异步交互与 DOM 动态渲染；
- 实现响应式页面布局，适配主流设备；
- 完成从需求 → 开发 → 联调 → 部署的完整前端交付流程。

功能预览
 - 首页: 商品分类展示、搜索框
 - 商品详情页:查看商品信息、加入购物车
 - 购物车页: 增删商品、修改数量、结算跳转
 - 订单确认页: 提交订单（调用后端接口）
 - 用户中心: 查看个人订单列表

当前 UI 以功能实现优先，后续可接入 CSS 框架（如 Bootstrap）优化视觉。

技术栈
- 核心语言：JavaScript (ES6+), HTML5, CSS3
- 数据交互：`fetch()` API 发起 AJAX 请求
- 页面路由：多 HTML 文件 + 手动跳转（无前端框架）
- 响应式设计：Flexbox + Media Queries
- 开发工具：VS Code, Live Server 插件
- 部署方式：Nginx 静态资源托管 / GitHub Pages

与后端联调
前端通过 AJAX 调用后端 RESTful 接口（默认地址：`http://localhost:8080`）：

```javascript
// 示例：获取商品列表
async function loadProducts() {
  try {
    const response = await fetch('http://localhost:8080/api/products?page=1&size=10');
    const data = await response.json();
    if (data.code === 200) {
      renderProductList(data.data);
    }
  } catch (error) {
    console.error('加载商品失败:', error);
  }
}
