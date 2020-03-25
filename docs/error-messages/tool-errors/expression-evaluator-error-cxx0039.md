---
title: 表达式计算器错误 CXX0039
ms.date: 11/04/2016
f1_keywords:
- CXX0039
helpviewer_keywords:
- CXX0039
- CAN0039
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
ms.openlocfilehash: 5706d002eb3d566d05b059cb04b6b1626fdb3d33
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185121"
---
# <a name="expression-evaluator-error-cxx0039"></a>表达式计算器错误 CXX0039

符号不明确

C 表达式计算器无法确定要在表达式中使用的符号实例。 符号在继承树中出现多次。

必须使用范围解析运算符（`::`）显式指定要在表达式中使用的实例。

此错误与 CAN0039 相同。
