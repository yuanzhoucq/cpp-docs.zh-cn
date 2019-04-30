---
title: 表达式计算器错误 CXX0017
ms.date: 11/04/2016
f1_keywords:
- CXX0017
helpviewer_keywords:
- CAN0017
- CXX0017
ms.assetid: af74db02-a64d-49ca-8363-3e044a107580
ms.openlocfilehash: bbf16ae9a503a8525edb42d6bf1fc4336c3f5267
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397128"
---
# <a name="expression-evaluator-error-cxx0017"></a>表达式计算器错误 CXX0017

未找到符号

找不到表达式中指定的符号。

此错误的一个可能的原因是中的符号名称的大小写不匹配。 因为 C 和C++都是区分大小写的语言，必须在其中它定义在源中的正确大小写中给定的符号名称。

尝试进行类型转换以在调试期间监视变量的变量时，可以发生此错误。 `typedef`声明类型的新名称，但不定义新类型。 尝试在调试器中的类型转换需要已定义的类型的名称。

此错误是与 CAN0017 相同。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 请确保符号已在其中使用的程序中的点声明。

1. 使用实际类型名来将变量强制转换在调试器中，而非`typedef`-定义的名称。