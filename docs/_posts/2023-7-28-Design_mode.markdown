---
layout: post
title:  "设计模式"
date:   2023-7-28 16:00:59 +0800
categories: jekyll update
---

* content
{:toc}

# 一些名词
## 类爆炸
### 定义
类爆炸不是指类的具体数量的多少，而是指在实现一个功能时，类本来可以不用这么多，但是却设计成这么多，使得维护成本过高，明显高于设计的效用。
### 原因
类爆炸的产生原因我的理解可总结为以下几点

1.产生类爆炸主要是对于设计模式或者说面向对象原则的过度使用造成的，无论是面向拓展开放，面向修改封闭其他的一些面向对象设计原则的过度使用都是造成类爆炸的原因

2.太过于遵守单一职责原则，使得类的粒度太小。

3.依赖接口而非依赖类的原则，为了低耦合和复用，抽象粒度过小，相同功能的代码。抽象粒度越小，类则越多。比如说本来有A,B,C,D四个类。然后为了低耦合高复用，把A，B的共同点抽象出来放在类E中，把C，D的共同点抽象出来放在类F中，然后再把E，F的共同点抽象出来放在G中，那么本来可以四个类完成的功能，现在为了低耦合和复用变成了7个类。

## 透明围栏(Transparent Enclosure)
1）单子女（单组件）组合；2）兼容的接口
4.在可以使用组合的情况下，使用了继承，而使得类太多。比如装饰者模式，就可以解决某些场景下的类爆炸问题。
# 简单了解部分模式
## composite 组合模式
由一个含有基本的信息作为类（Composition），在通过封装另一个类（Compositor）进行格式化。
## Strategy 策略模式
在对象中封装算法是 Strategy模式的目的。
模式的主要参与者是 Strategy对象（这些对象中封装了不同的算法）和它们的操作环境。
其实Compositor就是Strategy。它们封装了不同的格式算法。Composition就是Compositor策略的环境。 
## Decorator 装饰模式
修饰指给一个对象增加职责的事物。
## Abstract Factory 抽象工厂模式
工厂（Factory）和产品（Product）是Abstract Factory模式的主要参与者。
该模式描述了怎样在不直接实例化类的情况下创建一系列相关的产品对象。
它最适用于产品对象的数目和种类不变，而具体产品系列之间存在不同的情况。
## Command 命令模式
封装变化
## Iterator 迭代器模式
封装分析
## Visitor 访问者模式
该模式最适合于当你想对一个稳定类结构的对象做许多不同的事情的情况。
# 创建型模式
创建型模式显示如何使得这个设计更灵活，但未必会更小。特别是，它们将便于修改定义一个迷宫构件的类。
## ABSTRACT FACTORY 抽象工厂模式（对象创建性）
1: 意图<br />
提供一个创建一系列相关或相互依赖对象的接口，而无需指定它们具体的类。

2: 动机<br />
考虑一个支持多种视感（look-and-feel）标准的用户界面工具包。

3: 适用性<br />
在以下情况可以使用Abstract Factory模式
• 一个系统要独立于它的产品的创建、组合和表示时。
• 一个系统要由多个产品系列中的一个来配置时。
• 当你要强调一系列相关的产品对象的设计以便进行联合使用时。
• 当你提供一个产品类库，而只想显示它们的接口而不是实现时。

4:参与者<br />
• AbstractFactory(WidgetFactory)<br />
— 声明一个创建抽象产品对象的操作接口。<br />
• ConcreteFactory(MotifWidgetFactory，PMWidgetFactory)<br />
— 实现创建具体产品对象的操作。<br />
• AbstractProduct(Windows，ScrollBar)<br />
— 为一类产品对象声明一个接口。<br />
• ConcreteProduct(MotifWindow，MotifScrollBar)<br />
— 定义一个将被相应的具体工厂创建的产品对象。<br />
— 实现Abstract Product接口。<br />
• Client<br />
— 仅使用由AbstractFactory和AbstractProduct类声明的接口。<br />

5:实现<br />
• 将工厂作为单件，一个应用中一般每个产品只有一个ConcreteFactory的实例，因此最好实现为一个Singleton
• 创建产品Abstract Factory仅声明一个创建产品的接口 ，真正创建产品是由
ConcreteProduct子类实现的。最通常的一个办法是为每一个产品定义一个工厂方法
• • • 
