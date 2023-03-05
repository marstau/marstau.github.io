---
layout: post
title: Behaviour Tree
category: 编程开发
tags: algorithm
keywords: 
description: 
---

## 基础逻辑[More](https://blog.51cto.com/u_15304158/3142421)

--顺序节点（Sequence）：组合节点，顺序执行子节点，只要碰到一个子节点返回FALSE，则返回FALSE；否则返回TRUE。

--选择节点（Selector）：组合节点，顺序执行子节点，只要碰到一个子节点返回TRUE，则返回TRUE；否则返回FALSE。

--条件节点（Condition）：叶节点，执行条件判断，返回判断结果。

--执行节点（Action）：叶节点，执行设定的动作，一般返回TRUE。

## 复合节点(composite)

在行为树中，复合节点是用来组合其他节点的节点。复合节点是行为树中的一个重要概念，它允许我们在行为树中组织和管理大量节点。

Sequence: 类似And操作, 按顺序执行所有子节点，如果有一个节点失败，则整个顺序节点失败，所有成功则返回成功。

Parallel: 与Sequence类似，但是是并行运行所有子节点, 一个返回失败,则终止其他子节点运行, 并返回失败。

ParallelSelector: 并行运行所有子节点, 一个返回成功则终止其他子节点运行，并返回成功, 所有失败才返回失败。

ParallelComplete: 类似ParallelSelector, 唯一不同的是不论子节点返回成功失败，只要其中一个返回了就立刻返回。

Selector: 类似Or操作, 按顺序执行所有子节点，有一个节点返回成功,则立刻返回成功，所有失败则返回失败。

SelectorEvaluator: 

RandomSelector:

RandomSequence:

## 修饰符(decorator)

在行为树中，修饰符是一种节点类型，它可以修改其子节点的行为或结果。

修饰符有以下几种类型：

Inverter（反转器）：将其子节点的结果反转，如果子节点返回 True，则返回 False，反之亦然。

Succeeder（成功器）：将其子节点的结果转换为 True，无论其子节点返回什么结果。

Repeater（重复器）：可以无限循环地运行其子节点，或者重复执行一定次数，直到其子节点返回指定的结果。

UntilFail（直到失败）：持续运行其子节点，直到子节点返回 False。

UntilSuccess（直到成功）：持续运行其子节点，直到子节点返回 True。

LimitOfExecutions（执行次数限制器）：限制其子节点执行的次数，可以指定次数上限或时间上限。

这些修饰符可以让行为树更加灵活，根据需要对节点进行修改和组合，从而实现复杂的行为逻辑。

ConditionalEvaluator: 

"Evaluates the specified conditional task. If the conditional task returns success then the child task is run and the child status is returned. If the conditional task does not " +
                     "return success then the child task is not run and a failure status is immediately returned."

## Reference

* <https://zhuanlan.zhihu.com/p/92298402>
* <https://blog.csdn.net/u012740992/article/details/79366251>
* <https://blog.csdn.net/linxinfa/article/details/72937709>