<div align="center">

# IC Layout Design Projects
### 基于 SMIC 0.18μm 工艺的定制化模拟与标准单元版图设计实验

[![Process](https://img.shields.io/badge/Process-SMIC%200.18μm-blue)](https://www.smics.com/)
[![Tools](https://img.shields.io/badge/EDA-Cadence%20Virtuoso%20%7C%20Spectre%20%7C%20Calibre-orange)](https://www.cadence.com/)
[![License](https://img.shields.io/badge/License-Apache2.0-green)](LICENSE)

**全流程闭环实践：从标准单元表征到复杂模拟核心验证** Full flow practice: Standard cell → Passive array → Analog core (Bandgap)

</div>

---

## 项目亮点 (Highlights)

- 基于真实流片工艺 **SMIC 0.18μm**
- 完整验证链路：Schematic → Symbol → Testbench → Layout → DRC/LVS/PEX → Pre/Post sim
- 包含三种典型模块：**高驱动反相器 INV10X**、**高密度电容阵列**、**带隙基准核心**
- 版图注重**匹配、对称性、dummy 填充、via 阵列优化**

## 实验环境 (Design Environment)
- **工艺**：SMIC 0.18μm 1P6M CMOS
- **主要工具**：
  - Cadence Virtuoso (schematic & layout)
  - Spectre (simulation)
  - Calibre / Assura (DRC / LVS / PEX)
- **验证项目**：DRC / LVS / PEX / Pre- vs Post-layout simulation comparison

---

## 🛠 实验一：INV10X 版图设计与后仿真 (INV10X Layout Design and Post-Simulation)

本实验设计了一个具有 10 倍驱动能力的反相器。根据设计规范，配置 NMOS 和 PMOS 的宽长比均为 $5\mu\text{m} / 0.25\mu\text{m}$。

<details open>
<summary>展开查看详细步骤与结果</summary>

<div align="center">
  <img src="images/inv10x_schematic.png" alt="INV10X Schematic" width="50%"/>
  <p><i>图 1.1: INV10X 原理图</i></p>
  
  <img src="images/inv10x_symbol.png" alt="INV10X Symbol" width="50%"/>
  <p><i>图 1.2: INV10X 符号图</i></p>
  
  <img src="images/inv10x_testbench.png" alt="Simulation Testbench" width="50%"/>
  <p><i>图 1.3: 前/后仿真测试平台</i></p>
  
  <img src="images/inv10x_pre_sim_wave.png" alt="Pre-layout Simulation Waveform" width="50%"/>
  <p><i>图 1.4: 前仿真波形</i></p>

  <img src="images/inv10x_layout.png" alt="INV10X Layout" width="50%"/>
  <p><i>图 1.5: INV10X 版图 (采用 Multi-finger 结构)</i></p>
  
  <img src="images/inv10x_drc_report.png" alt="DRC Report" width="50%"/>
  <p><i>图 1.6: DRC 检查报告 (Clean)</i></p>
  
  <img src="images/inv10x_lvs_report.png" alt="LVS Report" width="50%"/>
  <p><i>图 1.7: LVS 检查报告 (Match)</i></p>
  
  <img src="images/inv10x_post_sim_wave.png" alt="Post-layout Simulation Waveform" width="50%"/>
  <p><i>图 1.8: 后仿真波形 (含寄生参数)</i></p>
  
  <img src="images/inv10x_sim_comparison.png" alt="Pre vs Post Comparison" width="50%"/>
  <p><i>图 1.9: 前后仿真性能对比</i></p>
</div>

</details>

---

## 💎 实验二：电容阵版图设计 (Capacitor Array Layout Design)

电容基本单元 C0 (Basic Unit C0)
基本单元大小为 $5\mu\text{m} \times 5\mu\text{m}$，利用 M1-M5 金属层构成 MIM/MOM 结构。

<details open>
<summary>展开查看详情</summary>

<div align="center">
  <img src="images/cap_unit_c0_layout.png" alt="C0 Unit Layout" width="50%"/>
  <p><i>图 2.1: 基本电容单元 C0 版图</i></p>
  
  <img src="images/cap_unit_c0_drc.png" alt="C0 DRC" width="50%"/>
  <p><i>图 2.2: C0 单元 DRC 结果</i></p>
  
  <img src="images/cap_array_10x20_layout.png" alt="10x20 Capacitor Array Layout" width="50%"/>
  <p><i>图 2.3: C10×20 电容阵列版图</i></p>
  
  <img src="images/cap_array_10x20_drc.png" alt="Array DRC" width="50%"/>
  <p><i>图 2.4: 电容阵列 DRC 结果</i></p>
</div>

</details>

---

## 🧪 实验三：带隙参考源核心电路 (Bandgap Reference Core Circuit)

实现带隙参考源核心电路的版图设计与验证。

<details open>
<summary>展开查看详情</summary>

<div align="center">
  <img src="images/bgr_core_schematic.png" alt="BGR Core Schematic" width="50%"/>
  <p><i>图 3.1: 带隙基准核心原理图</i></p>
  
  <img src="images/bgr_core_layout.png" alt="BGR Core Layout" width="50%"/>
  <p><i>图 3.2: 带隙基准核心版图 (采用匹配技术)</i></p>
  
  <img src="images/bgr_core_drc.png" alt="BGR DRC" width="50%"/>
  <p><i>图 3.3: 带隙核心 DRC 结果</i></p>
  
  <img src="images/bgr_core_lvs.png" alt="BGR LVS" width="50%"/>
  <p><i>图 3.4: 带隙核心 LVS 结果</i></p>
</div>

</details>

---

## 总结与感悟 (Lessons Learned & Conclusion)

通过本次 SMIC 0.18μm 版图设计实战，我不仅掌握了 EDA 工具的使用，更深刻理解了“物理实现”对电路性能的决定性作用。

### 1. 寄生参数对性能的影响 (Impact of Parasitics)
在 **INV10X** 的后仿真阶段，可以直观地观察到由于金属连线和过孔产生的**寄生电阻与电容**：
* **信号延迟**：后仿真波形较前仿真有明显的相位滞后。
* **电压降**：在高驱动电流下，布线阻抗导致的 IR Drop 会微弱影响输出摆幅。
* **感悟**：优秀的版图工程师必须在面积（Area）与寄生（Parasitics）之间寻找最优平衡点。

### 2. 高级模拟匹配策略 (Precision Analog Matching)
针对 **BGR (带隙基准源)** 核心电路，实验验证了匹配技术是模拟版图的灵魂：
* **共重心布局 (Common-Centroid)**：通过将 BJT 阵列进行交叉对称排列，抵消了晶圆生产中不可避免的线性工艺梯度（Process Gradient），是保证基准电压 $V_{ref}$ 稳定性的基石。

* **Dummy 填充**：在匹配阵列边缘添加非工作单元，补偿了刻蚀负载效应（Etch Loading Effect），确保核心器件的物理形貌高度一致。

### 3. 可靠性与噪声屏蔽 (Reliability & Noise Immunity)
实验中通过引入 **保护环 (Guard Ring)** 显著提升了电路的健壮性：
* **噪声隔离**：保护环如同“收集器”，能有效捕获衬底中的注入电荷，防止数字噪声耦合至敏感的基准模块。
* **防锁定效应 (Anti-Latch-up)**：通过降低衬底电阻，破坏寄生晶闸管的触发条件，大幅降低了芯片在复杂电磁环境下烧毁的风险。


---

**通过本系列实验，我建立起了从电路原理图（Schematic）到物理版图（Layout），再到后仿真验证（Post-Sim）的完整闭环思维，深刻认识到模拟版图设计是工艺、物理与艺术的结合。**

**Schematic wins on paper, Layout wins in silicon**
