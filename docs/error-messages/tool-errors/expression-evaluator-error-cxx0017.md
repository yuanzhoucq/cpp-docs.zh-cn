---
title: 表达式计算器错误 CXX0017
ms.date: 11/04/2016
f1_keywords:
- CXX0017
helpviewer_keywords:
- CAN0017
- CXX0017
ms.assetid: af74db02-a64d-49ca-8363-3e044a107580
ms.openlocfilehash: 64ebce0161d67c298d55095f6bc409820120c34a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196009"
---
# <a name="expression-evaluator-error-cxx0017"></a>表达式计算器错误 CXX0017

找不到符号

找不到表达式中指定的符号。

此错误的一个可能原因是符号名称不匹配。 因为 C 和C++都是区分大小写的语言，所以必须以其在源中定义的完全相同的形式提供符号名称。

尝试转换变量以在调试过程中监视变量时，可能会发生此错误。 `typedef` 声明类型的新名称，但不定义新类型。 在调试器中尝试的转换需要定义的类型的名称。

此错误与 CAN0017 相同。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复

1. 请确保已在使用该符号的程序中的点声明符号。

1. 使用实际类型名称来强制转换调试器中的变量，而不是 `typedef`定义的名称。
