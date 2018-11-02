---
title: 表达式计算器错误 CXX0015
ms.date: 11/04/2016
f1_keywords:
- CXX0015
helpviewer_keywords:
- CXX0015
- CAN0015
ms.assetid: 35efaf77-d578-48d8-bfc5-fdeb2a46a8b5
ms.openlocfilehash: f73aef18563426d28a81b92b3c37d1b7e345d0d3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662037"
---
# <a name="expression-evaluator-error-cxx0015"></a>表达式计算器错误 CXX0015

表达式过于复杂 （堆栈溢出）

输入的表达式是过于复杂或嵌套太深所个 C 表达式计算器的可用存储量。

由于过多挂起的计算，通常会出现溢出。

重新排列该表达式，以便时遇到，可以计算表达式的每个组件，而不必等待要计算的表达式的其他部分。

将表达式拆分为多个命令。

此错误是与 CAN0015 相同。