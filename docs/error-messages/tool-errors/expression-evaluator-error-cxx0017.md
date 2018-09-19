---
title: 表达式计算器错误 CXX0017 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0017
dev_langs:
- C++
helpviewer_keywords:
- CAN0017
- CXX0017
ms.assetid: af74db02-a64d-49ca-8363-3e044a107580
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 431071137fb3f5b1b276327ee7d21f323ac24c5b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46136228"
---
# <a name="expression-evaluator-error-cxx0017"></a>表达式计算器错误 CXX0017

未找到符号

找不到表达式中指定的符号。

此错误的一个可能的原因是中的符号名称的大小写不匹配。 因为 C 和 c + + 是区分大小写的语言，必须在其中它定义在源中的正确大小写中给定的符号名称。

尝试进行类型转换以在调试期间监视变量的变量时，可以发生此错误。 `typedef`声明类型的新名称，但不定义新类型。 尝试在调试器中的类型转换需要已定义的类型的名称。

此错误是与 CAN0017 相同。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 请确保符号已在其中使用的程序中的点声明。

1. 使用实际类型名来将变量强制转换在调试器中，而非`typedef`-定义的名称。