---
title: 表达式计算器错误 CXX0039
ms.date: 11/04/2016
f1_keywords:
- CXX0039
helpviewer_keywords:
- CXX0039
- CAN0039
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
ms.openlocfilehash: 053e57a21f0cb75cbd96732edb6812b3557bcd50
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396972"
---
# <a name="expression-evaluator-error-cxx0039"></a>表达式计算器错误 CXX0039

符号不明确

C 表达式计算器无法确定哪些实例要在表达式中使用的符号。 该符号在继承树中多次出现。

必须使用范围解析运算符 (`::`) 来显式指定要在表达式中使用的实例。

此错误是与 CAN0039 相同。