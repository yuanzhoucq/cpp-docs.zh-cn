---
title: 表达式计算器错误 CXX0030
ms.date: 11/04/2016
f1_keywords:
- CXX0030
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
ms.openlocfilehash: 477ec31d18924e91baf2d8b7b732bc7a50eee53b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195612"
---
# <a name="expression-evaluator-error-cxx0030"></a>表达式计算器错误 CXX0030

表达式 not evaluatable

调试器的表达式计算器无法获取所写入表达式的值。 其中一种可能的原因是表达式引用的内存不在程序的地址空间（取消引用 null 指针是一个示例）。 Windows 不允许访问位于程序的地址空间以外的内存。

您可能想要使用括号重写表达式，以控制计算的顺序。

此错误与 CAN0030 相同。
