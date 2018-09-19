---
title: 表达式计算器错误 CXX0065 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0065
dev_langs:
- C++
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c100b1edbd36f4384e8deb1abf5b36465e8da479
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024159"
---
# <a name="expression-evaluator-error-cxx0065"></a>表达式计算器错误 CXX0065

变量需要堆栈帧

表达式包含的当前作用域中存在但尚未创建的变量。

当您单步执行函数但尚未设置函数的堆栈帧的序言或你单步执行函数的退出代码，可以发生此错误。

逐句通过 prolog 代码直到对表达式求值之前设置的堆栈帧。

此错误是与 CAN0065 相同。