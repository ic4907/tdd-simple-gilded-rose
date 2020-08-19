# TDD @Gilded Rose

![Build](https://github.com/xpbootcamp/tdd-gilded-rose/workflows/Build/badge.svg)

## 开发环境
 - JDK1.8+
 
## 业务需求

"镶金玫瑰"！这是一家魔兽世界里的小商店。出售的商品也都是高质量的。但不妙的是，随着商品逐渐接近保质期，它们的质量也不断下滑。我们用一个IT系统来更新库存信息。

首先，简单介绍一下我们的系统：

- 所有商品都有一个`SellIn`值，这是商品距离过期的天数，最好在这么多天之内卖掉
- 所有商品都有一个`Quality`值，代表商品的价值
- 商品的`SellIn`值和`Quality`值，它们每天会发生变化


商品的价格规则说明如下：

- 商品的价值永远不会小于0，也永远不会超过50
- 普通商品每过一天价值会下滑一点，一旦过了保质期，价值就以双倍的速度下滑
- 后台门票（`Backstage pass`）是一种特殊商品：
	- 越接近演出日，商品的价值反而上升
	- 在演出前10天，价值每天上升2点
	- 演出前5天，价值每天上升3点
	- 一旦过了演出日，价值就马上变成0

### 验收数据
下面的数据用来验收你的代码是否满足客户的期望

- sellIn：商品距离过期的天数，最好这么多天之内卖完
- quality：商品当前的价值
- updatedSellIn：经过n (sellIn - updatedSellIn) 天后，距离商品过期的天数
- updatedQuality: 经过n (sellIn - updatedSellIn) 天后, 商品的最新价值

#### 普通商品
sellIn, quality, updatedSellIn, updatedQuality
10, 20, 9, 19
2, 0, 1, 0
3, 6, 2, 5
0, 6, -1, 4
-1, 6, -2, 4

#### 后台门票
sellIn, quality, updatedSellIn, updatedQuality
15, 20, 14, 21
10, 45, 9, 47
9, 45, 8, 47
10, 49, 9, 50
10, 50, 9, 50
5, 49, 4, 50
5, 45, 4, 48
1, 20, 0, 23
0, 20, -1, 0

