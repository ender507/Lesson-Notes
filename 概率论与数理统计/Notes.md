# 概统笔记
## 样本及抽样分布


----------------------------------
--------------------------------

## 参数估计
### 点估计
#### 矩估计法
1. 设置总体X的k阶矩（以2为例）($μ_k=E(X^k)$)
   - $μ_1=E(X)$
   - $μ_2=E(X^2)=D(X)+[E(X)]^2$
2. 通过确定的分布F(x)，建立F(x)中参数与各个μ之间的关系，并解出各个参数=关于μ的方程
3.  使用 A<sub>l</sub> 代替 μ<sub>l</sub> ，其中$A_l=\frac{1}{n}\sum^n_{i=1}X_i^l$
    - $A_1=\overline{X}$
    - $A_2-A_1^2=\frac{1}{n}\sum^n_{i=1}X_i^2-\overline{X}^2=\frac{1}{n}\sum^n_{i=1}(X_i-\overline{X})^2$
-----------------------
#### 最大似然估计法
对于n个样本X<sub>1</sub>~X<sub>n</sub>，概率密度都为f(x;θ)
1. 求似然函数$L(θ)=\Pi^n_{i=1}f(x_i;θ)$
2. 求似然函数的最大值点。可求解$\frac{d}{dθ}L(θ)=0$或$\frac{d}{dθ}lnL(θ)=0$
------------------------------------
#### 无偏估计
- 无偏性：若$E(\hat{θ})=θ$则$\hat{θ}$为θ的无偏估计量
- 有效性：若θ<sub>1</sub>和θ<sub>2</sub>同为θ的无偏估计量，而$D(θ_1)\leq D(θ_2)$则前者更有效
- 相和性：对任意ε>0都有$^{lim}_{n->\inf}P(|\hat{θ}-θ|<ε)=0)$则θ帽是θ的相合估计量。
-----------------------------------
#### 区间估计
![参数估计](https://github.com/ender507/Lesson-Notes/blob/master/%E6%A6%82%E7%8E%87%E8%AE%BA%E4%B8%8E%E6%95%B0%E7%90%86%E7%BB%9F%E8%AE%A1/%E5%8F%82%E6%95%B0%E4%BC%B0%E8%AE%A1.jpg)

其中，分布$Z_\alpha$表示使得$Φ(x)=1-\alpha$的x值

-----------------------------------
-----------------------------------

## 假设检验
### 正态总体均值、方差的检验
![pic1](https://github.com/ender507/Lesson-Notes/blob/master/%E6%A6%82%E7%8E%87%E8%AE%BA%E4%B8%8E%E6%95%B0%E7%90%86%E7%BB%9F%E8%AE%A1/%E5%81%87%E8%AE%BE%E6%A3%80%E9%AA%8C1.jpg)

![pic2](https://github.com/ender507/Lesson-Notes/blob/master/%E6%A6%82%E7%8E%87%E8%AE%BA%E4%B8%8E%E6%95%B0%E7%90%86%E7%BB%9F%E8%AE%A1/%E5%81%87%E8%AE%BE%E6%A3%80%E9%AA%8C2.jpg)

其中，$t_{1-\alpha}(n_1,n_2)=\frac{1}{t_{\alpha}(n_2,n_1)}$

---------------------------------------
### 分布拟合检验
前提：n>=50，np<sub>i</sub>>=5，否则进行A<sub>i</sub>的合并
1. - H<sub>0</sub> : 总体X的分布函数为F(x)
   - H<sub>1</sub> : 总体X的分布函数不为F(x)
2. 列卡方拟合检验计算表。每一列分别为：
   - A<sub>i</sub> : 每种事件，对应X的不同取值
   - f<sub>i</sub> : 事件 A<sub>i</sub> 发生的次数
   - p<sub>i</sub> : F(x)分布中的预期发生概率
   - np<sub>i</sub> : 前两项的乘积，小于5要合并
   - $f^2_i/(np_i)$,最下面写上总和∑=...
3. - 检验统计量：$\chi^2=\sum^k_{i=1}\frac{f^2_i}{np_i}-n$
   - 拒绝域：$\chi^2\geq\chi^2_\alpha(k-r-1)$,其中，r为估计参数的个数。

-----------------------------------
-----------------------------------

## 方差分析及回归分析
### 单因素试验
#### 差异性判断
水平有s个，在水平A<sub>j</sub>下，有n<sub>j</sub>个样本,显著性水平为α
1. 假设检验：
   - H<sub>0</sub> : μ<sub>1</sub> = μ<sub>2</sub> = ... = μ<sub>s</sub>
   - H<sub>1</sub> : μ<sub>1</sub>，μ<sub>2</sub>，... μ<sub>s</sub>不全相等
2. 计算方差：
   - $S_T=\sum_{j=1}^s \sum_{i=1}^{n_j}X^2_{ij}-\frac{T^2_{..}}{n}$ (所有数的平方和-总和的平方/n)
   - $S_A=\sum_{j=1}^s \frac{T^2_{.j}}{n_j}-\frac{T^2_{..}}{n}$ (每一水平下的和的平方/水平样本数之和-总和的平方/n)
   - $S_E=S_T-S_A$
3. 方差分析表

方差来源|平方和|自由度|均方|F比
:-:|:-:|:-:|:-:|:-:
因素A|S<sub>A</sub>|s-1|平方和/自由度|S<sub>A</sub>均方/S<sub>E</sub>均方
误差|S<sub>E</sub>|n-s|平方和/自由度|
总和|S<sub>T</sub>|n-1
4. 拒绝域：$F\geq F_\alpha(s-1,n-s)$
#### 未知参数估计
μ<sub>j</sub> - μ<sub>k</sub> 置信水平为 1-α 的置信区间：

$(\overline X_{.j}-\overline X_{.k}\pm t_{\alpha /2}(n-s))\sqrt{\overline S_E(\frac{1}{n_j}+\frac{1}{n_k})}$

------------------------------------------------
### 双因素实验
水平A、B分别有r、s个.每组确定水平A<sub>i</sub>B<sub>j</sub>下有t个样本，显著性水平为α
1. 假设检验：
   - H<sub>01</sub> : α<sub>1</sub> = α<sub>2</sub> = ... = α<sub>r</sub> = 0
   - H<sub>11</sub> : α<sub>1</sub>，α<sub>2</sub>，... α<sub>r</sub>不全为0
   - H<sub>02</sub> : β<sub>1</sub> = β<sub>2</sub> = ... = β<sub>s</sub> = 0
   - H<sub>12</sub> : β<sub>1</sub>，β<sub>2</sub>，... β<sub>s</sub>不全为0   
   - H<sub>03</sub> : γ<sub>11</sub> = γ<sub>12</sub> = ... = γ<sub>rs</sub> = 0
   - H<sub>13</sub> : γ<sub>11</sub>，γ<sub>12</sub>，... γ<sub>rs</sub>不全为0
2. 计算方差：
   - $S_T=\sum_{i=1}^r \sum_{j=1}^s \sum_{k=1}^{t}X^2_{ijk}-\frac{T^2_{...}}{rst}$ (所有数的平方和-总和的平方/n)
   - $S_A=\frac{1}{st}\sum_{i=1}^r T^2_{i..}-\frac{T^2_{...}}{rst}$ (每一 水平A下的和的平方/该水平样本数 之和-总和的平方/n)
   - $S_B=\frac{1}{rt}\sum_{j=1}^s T^2_{.j.}-\frac{T^2_{...}}{rst}$ (每一 水平B下的和的平方/该水平样本数 之和-总和的平方/n)- 
   - $S_{A\times B}=(\frac{1}{t}\sum_{i=1}^r\sum_{j=1}^sT^2_{ij.}-\frac{T^2_{...}}{rst})-S_A-S_B$
   - $S_E=S_T-S_A-S_B-S_{A\times B}$
3. 方差分析表

方差来源|平方和|自由度|均方|F比
:-:|:-:|:-:|:-:|:-:
因素A|S<sub>A</sub>|r-1|平方和/自由度|S<sub>A</sub>均方/S<sub>E</sub>均方
因素B|S<sub>B</sub>|s-1|平方和/自由度|S<sub>B</sub>均方/S<sub>E</sub>均方
交互作用AxB|S<sub>AxB</sub>|(r-1)(s-1)|平方和/自由度|S<sub>AxB</sub>均方/S<sub>E</sub>均方
误差|S<sub>E</sub>|rs(t-1)|平方和/自由度|
总和|S<sub>T</sub>|rst-1
4. 拒绝域：
    - $F_A\geq F_\alpha(r-1,rs(t-1))$
    - $F_B\geq F_\alpha(s-1,rs(t-1))$
    - $F_{A\times B}\geq F_\alpha((r-1)(s-1),rs(t-1))$
---------------------------------
### 一元线性回归
$\hat{y}=\hat{a}+\hat{b}x$
1. 记号引入
   - $S_{xx}=\sum (x^2)-\frac{1}{n}(\sum x)^2$
   - $S_{yy}=\sum (y^2)-\frac{1}{n}(\sum y)^2$
   - $S_{xy}=\sum (xy)-\frac{1}{n}(\sum x)(\sum y)$
2. 回归方程的计算
   - $\hat{b}=\frac{S_{xy}}{S_{xx}}$
   - $\hat{a}=\frac{1}{n}\sum y-(\frac{1}{n}\sum x)\hat{b}$
3. 方差估计
   - $\hat{\sigma^2}=\frac{Q_e}{n-2}=\frac{1}{n-2}(S_{yy}-\hat{b}S_{xy})$
4. 显著性检验：显著性水平为α
   - H<sub>0</sub> : b = 0
   - H<sub>1</sub> : b != 0
   - 拒绝域(注意给$\sigma^2$开方)：$|t|=\frac{|\hat{b}|}{\hat{\sigma}}\sqrt{S_{xx}}\geq t_{\alpha/2}(n-2)$
5. b的置信区间：置信水平为1-α
   - $(\hat{b}\pm t_{\alpha/2}(n-2)\times\frac{\hat{\sigma}}{\sqrt{S_{xx}}})$
6. 回归函数μ(x)的置信区间:置信水平为1-α
   - $(\hat{a}+\hat{b}x_0\pm t_{\alpha/2}(n-2)\hat{\sigma}\sqrt{\frac{1}{n}+\frac{(x_0-\overline{x})^2}{S_{xx}}})$
7. 观察值Y的置信区间：置信水平为1-α
   - $(\hat{a}+\hat{b}x_0\pm t_{\alpha/2}(n-2)\hat{\sigma}\sqrt{1+\frac{1}{n}+\frac{(x_0-\overline{x})^2}{S_{xx}}})$
