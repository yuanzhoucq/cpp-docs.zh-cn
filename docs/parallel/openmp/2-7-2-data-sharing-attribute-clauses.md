---
title: 2.7.2 数据共享特性子句 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 47347d3c-18bd-441f-99cf-7737564c417f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4b8c53cace8d50f10fe638ea8604c46e457f69ee
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392501"
---
# <a name="272-data-sharing-attribute-clauses"></a>2.7.2 数据共享特性子句

多个指令接受允许用户控制区域的持续时间内的变量的共享属性的子句。 共享特性子句仅适用于出现子句的指令的词法范围中的变量。 并非所有以下子句允许使用所有指令。 在指令中有所描述有效的特定指令的子句的列表。

如果变量是可见时并行或遇到工作共享构造，并且不共享特性子句中指定的变量或**threadprivate**指令，然后变量共享的。 共享并行区域的动态范围内声明的静态变量。 堆分配的内存 (例如，使用**使用 malloc （)** C 或 c + + 或**新**c + + 中的运算符) 共享。 （指向此内存，但是，可以是私有或共享。）具有自动存储持续时间并行区域的动态范围内声明的变量是私有类型。

大部分子句接受*变量列表*参数，其是可见的变量的以逗号分隔的列表。 如果变量引用中的数据共享特性子句已从模板派生的类型和不没有给该变量在程序中的任何其他引用，该行为不确定。

在指令子句内出现的所有变量必须都是可见的。 子句中根据需要可能会重复，但可能在多个子句中，指定没有变量，只不过变量可以指定在这种**firstprivate**和一个**lastprivate**子句。

以下部分介绍了数据共享特性子句：

- **私有**，[部分 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md)第 25 页上。

- **firstprivate**，[部分 2.7.2.2](../../parallel/openmp/2-7-2-2-firstprivate.md)第 26 页上。

- **lastprivate**，[部分 2.7.2.3](../../parallel/openmp/2-7-2-3-lastprivate.md) 27 页上。

- **共享**，[部分 2.7.2.4](../../parallel/openmp/2-7-2-4-shared.md) 27 页上。

- **默认值**，[部分 2.7.2.5](../../parallel/openmp/2-7-2-5-default.md)扯下一页上。

- **减少**，[部分 2.7.2.6](../../parallel/openmp/2-7-2-6-reduction.md)扯下一页上。

- **copyin**，[部分 2.7.2.7](../../parallel/openmp/2-7-2-7-copyin.md)第 31 页。

- **copyprivate**，[部分 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md)第 32 页上。