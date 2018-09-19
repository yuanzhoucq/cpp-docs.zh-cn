---
title: 表达式计算器错误 CXX0039 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0039
dev_langs:
- C++
helpviewer_keywords:
- CXX0039
- CAN0039
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b5397426618c5dfcbaa6307105781ff2e6f2eb97
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048326"
---
# <a name="expression-evaluator-error-cxx0039"></a>表达式计算器错误 CXX0039

符号不明确

C 表达式计算器无法确定哪些实例要在表达式中使用的符号。 该符号在继承树中多次出现。

必须使用范围解析运算符 (`::`) 来显式指定要在表达式中使用的实例。

此错误是与 CAN0039 相同。