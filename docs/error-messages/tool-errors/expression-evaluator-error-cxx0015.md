---
title: 表达式计算器错误 CXX0015
ms.date: 11/04/2016
f1_keywords:
- CXX0015
helpviewer_keywords:
- CXX0015
- CAN0015
ms.assetid: 35efaf77-d578-48d8-bfc5-fdeb2a46a8b5
ms.openlocfilehash: 19cf47d6b7b718eb19b987bcc16854af3266069b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196061"
---
# <a name="expression-evaluator-error-cxx0015"></a>表达式计算器错误 CXX0015

表达式太复杂（堆栈溢出）

对于 C 表达式计算器可用的存储量，输入的表达式太复杂或嵌套太深。

由于挂起的计算过多，通常会发生溢出。

重新排列表达式，以便可以在表达式的每个组件遇到时进行计算，而不必等待表达式的其他部分计算。

将表达式拆分成多个命令。

此错误与 CAN0015 相同。
