---
name: canvas-app-refactor
description: 专门用于将Gemini Canvas等AI对话生成的单体JSX前端项目，重构为逻辑-表现-数据（MVC）分离的标准前端工程，且严格保证像素级还原。
---

# Canvas App Refactor Skill

## 目标与职责
当处理早期的实验性或从 AI 大语言模型（如 Gemini Canvas）生成的单体富应用 `.jsx`（如含有巨大代码量和重度内部状态依赖的 `App.jsx`）时，负责在不改变任何用户层 UI 与 UX 的前提下进行架构解耦。

## 设计拆解与执行标准

1. **像素级不变与无损操作**
   - **视觉无损**：严禁任意更改 Tailwind 类名层级与 CSS 内联逻辑，原始宽高和 Flex 弹性自适应机制一分不差予以保留。
   - **交互无损**：必须确保触屏 `touch`（双指 Pinch、拖拽）、`pointer` 悬停防抖等 UX 保留。（即不盲目重写全局浏览器原生事件监听机制）

2. **数据抽出 (Data Layer)**
   - 创建 `src/data/` 目录。
   - 提取业务常量定义（如卡牌字典、商品配置）。
   - 提取依赖运算的初始值字典工厂、甚至单文件内封装的类或 Mock 模拟数据。

3. **逻辑无头化与优化保留 (Logic Layer)**
   - 建设 `src/logic/engine/` 用于纯计算或核心统筹计算。
   - 建设 `src/logic/hooks/`，这是最关键一步。单文件中往往含有针对 `useEffect` 高频重绘（比如 50ms 心跳）触发的闭包陷阱（Stale Closure）。
   - **经验红线**：若原作中使用了 `useRef(state)` 的双重状态引用同步大法，千万**不要**随意改成普通依赖，必须以自定义 hook 形式保持这套能跑的性能同步引擎。

4. **展示拆片 (View Layer)**
   - 建立 `src/view/screens/` 级与 `src/view/components/` 级拆分。
   - 以原始大渲染树剥离片段，剔除业务依赖，将其设计成只认 props 的纯展示哑组件。

5. **组装主入口配置**
   - 引入 Vite (如 `npm i -D vite @vitejs/plugin-react` ...) 、补齐 TailwindCSS 基建补丁（`postcss`, `tailwind config`）。
   - 缩减 `App.jsx` 的作用直至其只剩下组合 Views 和接入 Hooks。