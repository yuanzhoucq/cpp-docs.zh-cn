---
title: 1.4 遵从性
ms.date: 11/04/2016
ms.assetid: 662ad260-b9a1-43b7-b269-ef6ff0714e05
ms.openlocfilehash: 7fb47c9989e971e10701c2ee2bd7ac7823141812
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642450"
---
# <a name="14-compliance"></a>1.4 遵从性

OpenMP C/c + + API 的实现*OpenMP 符合*如果它可以识别并为分布在各章 1，2，3，4，保留此规范的所有元素的语义和附录 C.附录 A、 B、 D、 E 和 F 适用于信息仅目的并不是规范的一部分。 包含 API 的一个子集的实现不符合 OpenMP 的。

OpenMP C 和 c + + API 是支持的实现的基本语言的扩展。 如果基础语言不在本文档中支持的语言构造或显示的扩展，OpenMP 实现不需要支持它。

所有标准的 C 和 c + + 库函数和内置函数 （即，编译器具有特定的知识的函数） 必须是线程安全的。 未同步的使用并行区域内的不同线程的线程安全函数不会产生未定义的行为。 但是，行为可能不是与串行区域中的相同。 （随机数字生成函数是一个示例。）

OpenMP C/c + + API 指定特定的行为是*实现定义。* 需要定义并记录在这些情况下其行为符合标准的 OpenMP 实现。 请参阅[附录 E](../../parallel/openmp/e-implementation-defined-behaviors-in-openmp-c-cpp.md)，页 97，为实现定义的行为的列表。