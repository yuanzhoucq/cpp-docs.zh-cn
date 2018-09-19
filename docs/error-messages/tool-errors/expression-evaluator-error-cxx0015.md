---
title: 表达式计算器错误 CXX0015 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0015
dev_langs:
- C++
helpviewer_keywords:
- CXX0015
- CAN0015
ms.assetid: 35efaf77-d578-48d8-bfc5-fdeb2a46a8b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1aa37a2cc7208063ce4cfa786de196842ab42b45
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050811"
---
# <a name="expression-evaluator-error-cxx0015"></a>表达式计算器错误 CXX0015

表达式过于复杂 （堆栈溢出）

输入的表达式是过于复杂或嵌套太深所个 C 表达式计算器的可用存储量。

由于过多挂起的计算，通常会出现溢出。

重新排列该表达式，以便时遇到，可以计算表达式的每个组件，而不必等待要计算的表达式的其他部分。

将表达式拆分为多个命令。

此错误是与 CAN0015 相同。