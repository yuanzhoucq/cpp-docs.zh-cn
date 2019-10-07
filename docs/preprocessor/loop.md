---
title: loop 杂注
ms.date: 08/29/2019
f1_keywords:
- loop_CPP
- vc-pragma.loop
ms.assetid: 6d5bb428-cead-47e7-941d-7513bbb162c7
ms.openlocfilehash: 013540ffe120f42c15538ce86661753b9cf9416f
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220845"
---
# <a name="loop-pragma"></a>loop 杂注

控制自动并行如何考虑循环代码, 或将循环排除在自动向量化的范围之外。

## <a name="syntax"></a>语法

> **#pragma 循环 (hint_parallel (** *n* **))** \
> **#pragma 循环 (no_vector)** \
> **#pragma 循环 (ivdep)**

### <a name="parameters"></a>参数

**hint_parallel (** *n* **)** \
对编译器的提示: 应跨*n*个线程并行化此循环, 其中*n*是一个正整数文本或零。 如果*n*为零, 则在运行时使用最大线程数。 这是对编译器的提示, 而不是命令。 不保证会并行化循环。 如果循环具有数据依赖关系或结构问题, 则不会对其进行并行化。 例如, 如果存储到在循环体之外使用的标量, 则不会对其进行并行化。

除非指定了[/Qpar](../build/reference/qpar-auto-parallelizer.md)编译器开关, 否则编译器将忽略此选项。

**no_vector**\
默认情况下, 自动向量化尝试特征矢量化其评估的所有循环可能会从中受益。 指定此杂注可禁用循环的自动向量化。

**ivdep**\
提示编译器忽略此循环的矢量依赖项的提示。 将此选项与**hint_parallel**一起使用。

## <a name="remarks"></a>备注

若要使用**loop**杂注, 请将其置于循环定义之前, 而不是循环定义。 杂注对它后面的循环的范围有效。 您可按任意顺序将多个杂注应用于一个循环，但必须在单独的杂注语句中声明每个杂注。

## <a name="see-also"></a>请参阅

[自动并行化和自动矢量化](../parallel/auto-parallelization-and-auto-vectorization.md)\
[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
