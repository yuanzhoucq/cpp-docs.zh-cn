---
title: 编译器错误 C2865
ms.date: 11/04/2016
f1_keywords:
- C2865
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
ms.openlocfilehash: dd4374c1a577c4c39c5dec107ed5025d7cdc79c2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201691"
---
# <a name="compiler-error-c2865"></a>编译器错误 C2865

"function"：非法比较 handle_or_pointer

您可以比较对[类和结构](../../extensions/classes-and-structs-cpp-component-extensions.md)或托管引用类型的引用，以确定它们是否引用相同的对象（= =）或其他对象（！ =）。

由于 .NET 运行时可能随时移动托管对象，因此不能对它们进行比较以便进行排序。
