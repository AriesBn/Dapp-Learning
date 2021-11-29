# Abracadabra.money

## 一、背景

1、传统的Defi应用有一个硬伤

- 头矿收益高，吸引流动性进入协议，大户疯狂挖提卖
- 之后大量卖压导致币价下跌、挖矿收益率降低，大量流动性抽走
- 这对协议本身发展是不利的

2、Defi2.0试图对流动性进行引导,将流动性留在协议中，Abracadabra就是Defi2.0的代表之一

## 二、简介

- Abracadabra的借贷功能与MakerDao类似，MakerDao只能抵押ETH借出稳定币DAI，Abracadabra支持使用计息代币(ibTKN)和若干单币种进行抵押借出Abracadabra协议发行的稳定币MIM
- Abracadabra支持存入指定的LP代币进行耕种(farming)获得Spell奖励
- 目前Abracadabra协议支持5条链![](C:\maint\workspace\Dapp-Learning3\defi\Abracadabra\Images\fivechains.png)

## 三、代币经济模型

​		Abracadabra.Money 有 3 种代币：（1）SPELL: 用来做激励的代币,也就是挖矿的奖励（2）sSPELL: 通过质押 SPELL 获得，用于享受分红和治理   （3）MIM: 与美元挂钩的稳定币

### 1、Spell代币分配

- 45%奖励给MIM-3LP3CRV池子流动性提供者
- 18%奖励给sushiswap上ETH-SPELL池子的流动性提供者
- 30%分四年给项目团队,
- 7%通过IDO分配，一般在uni上，一半在sushi上

### 2、sSpell代币

​		通过质押Spell代币获得,代表了你在Spell池子中的份额，池子会根据份额来分配红利(这些红利主要来自于利息和借款费用)，同时sSpell也会不断复利

### 3、MIM代币

​	MIM币价格的稳定依赖于市场(主要靠机器人套保)   

- ​    低于1美元时,那些抵押资产借出MIM的人就会去买MIM然后用于repay
- ​    高于1美元的时候,人们会抵押资产换出MIM到池子里面兑换USDC/USDT/DAI等

## 四、主要模块

![](C:\maint\workspace\Dapp-Learning3\defi\Abracadabra\Images\head.png)

### 1、存(农场)

存入LP代币可以获得Spell奖励，当然在不同链上可以存入的LP不同（看Abracadabra需要哪些流动性），例如你在sushi上提供了ETH-Spell 或者ETH-MIN的流动性,可以将这两个流动性LP代币存入Abracadabra中，获取Spell奖励。这是一个双赢的做法，协议挽留了流动性，用户获得了Spell奖励。

### 2、借

用户可以将普通代币(FTM、UST、FTT等)或者计息代币(yvWETH、xSuSHI)进行抵押，设置相应的借款比例，借出稳定币MIM,当抵押品价格下降过快时会面临被清算的风险(下图以yvUSDT为例)![](C:\maint\workspace\Dapp-Learning3\defi\Abracadabra\Images\borrow.png)
​        更激进的做法是加杠杆，循环借贷

### 3、循环借贷(加杠杆)

Abracadabra支持最多十次循环		

- 抵押价值100美元的yvUSDT,考虑到清算风险只借出90%价值(即只借出了价值90美元的MIM),之后将MIM换成USDT存入yVault中，获得价值90美元的yvUSDT

- 抵押价值90美元的yvUSDT,又借出90%价值，这次只能借出81美元的MIM

  ​	...

  ​	如此循环往复(下图中显示加了9.58倍的杠杆)

  ![](C:\maint\workspace\Dapp-Learning3\defi\Abracadabra\Images\levelage.png)

- 这些流程在Abracadabra中支持一次操作，完成多次循环

### 4、质押

 用户在将Spell质押,获得sSpell(目前只支持以太坊),用于收取借款利息和治理
​        例如：用户抵押价值100美元的资产,只能获得100美元的MIM，却要背负100.5美元的债务,这多出来的0.5美元就是给sSpell用户的

### 5、交换

Abracadabra在Curve上有稳定币兑换的池子，支持USDC/USDT/DAI和MIM的1:1兑换![](C:\maint\workspace\Dapp-Learning3\defi\Abracadabra\Images\CurveSwap.png)

## 五、参考链接

1. 网站：https://abracadabra.money/
2.  Abracadabra Twitter:https://twitter.com/MIM_Spell
3. 0xMerlin Twitter:https://twitter.com/0xM3rlin
4. Medium:https://abracadabramoney.medium.com/
5. Telegram 交流群:https://t.me/MIM_Spell
6. Discord服务器：https://discord.gg/wcsUNxYrFM
7. GitHub:https://github.com/Abracadabra-money/magic-internet-money
8. GitBook:https://docs.abracadabra.money/