---
title: 表达式计算器错误 CXX0021
ms.date: 11/04/2016
f1_keywords:
- CXX0021
helpviewer_keywords:
- CXX0021
- CAN0021
ms.assetid: d6c0c35a-16c2-42c0-a7d2-e910350a47f0
ms.openlocfilehash: a800deb6bacbcae8666a3abad08b87d4f027790f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195834"
---
# <a name="expression-evaluator-error-cxx0021"></a>表达式计算器错误 CXX0021

用作标量的 struct 或 union

表达式中使用了结构或联合，但未指定任何元素。

在操作结构或联合变量时，变量的名称可能会自行显示，无需字段限定符。 如果在表达式中使用结构或联合，则必须使用所需的特定元素进行限定。

指定要在表达式中使用其值的元素。

此错误与 CAN0021 相同。
