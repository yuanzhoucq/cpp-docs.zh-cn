---
title: 表达式计算器错误 CXX0065
ms.date: 11/04/2016
f1_keywords:
- CXX0065
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
ms.openlocfilehash: 7b62e42da2a74d910e2dc56ce2dfcb5cb38f2bfa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62299310"
---
# <a name="expression-evaluator-error-cxx0065"></a>表达式计算器错误 CXX0065

变量需要堆栈帧

表达式包含的当前作用域中存在但尚未创建的变量。

当您单步执行函数但尚未设置函数的堆栈帧的序言或你单步执行函数的退出代码，可以发生此错误。

逐句通过 prolog 代码直到对表达式求值之前设置的堆栈帧。

此错误是与 CAN0065 相同。