# DECO6500 A2 - Accessible Boarding Connected Functional Prototype

## 📱 Prototype 核心架构与功能说明

本项目严格按照 DECO6500 教学要求（**"Functional prototype with all core features"**），完整实现了**乘客端（Passenger App）与司机车载端（Driver Console）的双端闭环交互流程**。

---

## 🚀 快速启动与测试方法

### 方式一：直接双击打开（最简单）
直接在电脑上双击打开以下任意文件即可在浏览器运行：
* `/Users/mizupoi/Desktop/6500/test.html`
* 或 `/Users/mizupoi/Desktop/6500/prototype/test.html`

### 方式二：本地 HTTP 预览（支持跨窗口实时同步）
在终端运行：
```bash
cd /Users/mizupoi/Desktop/6500
python3 -m http.server 8088
```
然后在浏览器中访问：`http://localhost:8088/test.html`

---

## 🔄 端到端完整操作流程演示（Friday Presentation Flow）

| 阶段 | 界面视图 | 用户操作与系统反馈 |
| :--- | :--- | :--- |
| **乘客 Screen 1** | **Route 66 行程信息** | 页面显示 UQ Lakes 站、66 路公交、`Bus arriving in 5 mins`。点击 **`[Request Accessible Boarding]`**。 |
| **乘客 Screen 2** | **Assistance Request** | 勾选辅助选项（`I use a wheelchair` / `I require the boarding ramp` / `I may require driver assistance`）。点击 **`[Send Request to Driver]`**。 |
| **乘客 Screen 3** | **Live Confirmation** | 页面提示 `Driver has been notified` 与 `Bus arriving in 4 minutes`，显示等待状态。同时**右侧司机端中控台立即触发高优先级声音/视觉警报**。 |
| **司机 Screen 1** | **Incoming Request Alert** | 司机中控台显示：`Next stop: UQ Lakes`、`Wheelchair passenger waiting`、`Ramp required`。司机点击 **`[Acknowledge Request]`**。 |
| **司机 Screen 2** | **Accessible SOP Checklist** | 司机按照规范完成 5 步辅助标准（靠站平齐 $\rightarrow$ 留足时间 $\rightarrow$ 放下斜坡板 $\rightarrow$ 征得同意后协助 $\rightarrow$ 确认轮椅位固定）。完成后点击 **`[Boarding Complete]`**。 |
| **乘客 Screen 4** | **Micro-Feedback Survey** | 司机端完成后，**乘客手机端自动跳转到评价界面**。选择体验等级（`Easy` / `Some difficulty` / `Difficult`）并勾选具体归因（`Ramp` / `Felt rushed` / `Driver assistance` 等）。点击 **`[Submit]`**。 |
| **闭环数据流** | **Evaluation Logging** | 提交后进入 Thank You 页面，同时数据自动沉淀进顶部 **`Test Logs`** 抽屉，方便团队进行 A2 的 Layer 1 & Layer 2 用户评估分析！ |

---

## 🛠️ 核心交互亮点（拿 HD 评分要素）

1. **分屏双机联动（Dual Split View）**：在同一屏幕左边放 iPhone 乘客端，右边放车载 iPad 司机端，一人即可顺畅演示双端实时交互。
2. **多视图切换**：支持顶部一键切换 `Dual Split View` / `Passenger Only` / `Driver Only`。
3. **跨标签页/跨设备实时通信**：内置 `BroadcastChannel` 机制，支持在两台设备或两个浏览器标签页分别打开，实时无线同步。
4. **一键重置与测试日志（Test Run Logging）**：支持随时重置流程（`Reset Flow`），并记录每一轮实验数据。
