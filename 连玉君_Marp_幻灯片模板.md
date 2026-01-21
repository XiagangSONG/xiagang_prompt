---

marp: true

<!-- page_number: true -->
<!-- $size: 16:9 -->
<!-- $theme: gaia -->

---

![bg right:40% brightness:. sepia:50%](https://fig-lianxh.oss-cn-shenzhen.aliyuncs.com/ladybug-drop-of-water-rain-leaf-40731.jpeg)


<!-- footer: 连享会 · [直播课](http://lianxh.duanshu.com) &nbsp;  | &nbsp;  lianxh.cn &nbsp; | &nbsp; [去听课](https://lianxh.duanshu.com/#/brief/course/c3f79a0395a84d2f868d3502c348eafc) &nbsp;| &nbsp; [看课件](https://gitee.com/arlionn/Live)-->



#### [${\color{blue}{连享会·直播课}}$](http://lianxh.duanshu.com)

${\color{white}{a}}$
${\color{white}{a}}$

## Stata：动态面板数据模型

<br>

##### 连玉君 (中山大学)
arlionn@163.com

${\color{white}{a}}$

--- - --

**课件使用说明**

> [连享会 · 直播间](http://lianxh.duanshu.com) >>>  [动态面板数据模型](https://lianxh.duanshu.com/#/brief/course/c3f79a0395a84d2f868d3502c348eafc) >>> 点击【**课程表**】即可查看下载链接

- 直播幻灯片：**连玉君-动态面板模型.pdf** 
- 【Refs】文件件中存放了课程中涉及的多数文献
- 【Data】存放了课程中使用的数据文件
- Stata 重现文档: **Lian_DyPanel.rar**
  - 下载 「Lian_DyPanel.rar」，解压后放在【D:\Lec】文件夹下即可。 
  - 在 Stata 命令窗口中执行如下命令，即可打开重现文件. 
    `doedit D:\Lec\Lian_DyPanel\Lian_DyPanel.do`




--- ---

### 提纲

- 简介：应用场景
- 模型设定
- 估计方法
  - FD-GMM；SYS-GMM；纠偏 OLS
- 假设检验：序列相关检验；过度识别检验
- Stata 实操 1：模型估计
  - OLS, FE, IV, 2SLS, GMM 对比
  - 简单模拟分析
- 实证分析中的主要陷阱
  - 至少需要几年的数据？
  - 要做哪些检验？一直通不过怎么办？
  - 工具变量太多怎么办？

${\color{white}{a}}$

--- - --


### 简介：我的体重 1

$
(1) \quad y_{t} = \rho y_{t-1} + \varepsilon_{t}  
$

$
(2) \quad y_{t-1} = \rho y_{t-2} + \varepsilon_{t-1}
$

将  (2) 带入 (1):

$
(3) \quad y_{t} = \rho^{2} y_{t-2} + \rho\varepsilon_{t-1} + \varepsilon_{t}
$

$\cdots$

$
(4) \quad y_{t} = \rho^{40} y_{t-40} + \rho^{39}\varepsilon_{it-39} +  \cdots + \rho\varepsilon_{it-1} +\varepsilon_{t}
$

- **Q1：** $\text{Corr}(y_{it},y_{it-2})=0\ ?$, $\text{Corr}(y_{it},y_{it-4})=0\ ?$ 
- **Q2：** $\color{red}{\rho}$ 的含义是什么？

--- - --

### 简介：我的体重 2

$
y_{t} = \rho y_{t-1} + \varepsilon_{t} \qquad \qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\quad\ \ (1) \quad
$

<br>

$
y_{t} = \alpha + \rho y_{t-1} + x_{t}\beta + \varepsilon_{t}  \qquad\qquad\qquad\qquad\qquad\qquad\qquad\quad (1a) 
$

<br>

$
y_{it} = \alpha_i + \rho y_{it-1} + x_{it}\beta + \theta_t + \varepsilon_{it}  \quad\qquad\qquad\qquad\qquad\qquad\quad (1b) 
$ 

<br>

$
y_{it} = \alpha_i + \rho y_{it-1} + x_{it-1}\beta_1 + x_{it-2}\beta_2+ \theta_t + \varepsilon_{it}  \qquad\qquad\qquad\ (1c) 
$

<br>
<br>
<br>


--- - --


### 扩展：
- 消费行为的惯性
- 投资行为
  - Carstensen K, Toubal F. Foreign direct investment in Central and Eastern European countries: a dynamic panel analysis. Journal of Comparative Economics, 2004, 32(1): 3-22.
- 能源消费与经济增长 PVAR
  - Huang B N, Hwang M J, Yang C W. Causal relationship between energy consumption and GDP growth revisited: a dynamic panel data approach. Ecological Economics, 2008, 67(1): 41-54.
- 综述
  - Bond S R. Dynamic panel data models: A guide to micro data methods and practice. Portuguese Economic Journal, 2002, 1(2): 141-162. (Cited 3000+)
