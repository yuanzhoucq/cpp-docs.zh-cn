---
title: 表达式计算器错误 CXX0069 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0069
dev_langs:
- C++
helpviewer_keywords:
- CXX0069
ms.assetid: cf334b23-1e17-4d37-acc5-18597ee84164
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a3efb6432f536ecb929c8ff8670d31030b569b7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112728"
---
# <a name="expression-evaluator-error-cxx0069"></a>表达式计算器错误 CXX0069

变量需要堆栈帧

表达式计算器不能计算变量，因为它不会出现在堆栈帧。 原因可能是变量声明为内联函数的一部分。