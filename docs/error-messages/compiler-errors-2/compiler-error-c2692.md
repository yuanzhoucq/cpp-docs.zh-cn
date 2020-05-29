---
title: 编译器错误 C2692
ms.date: 11/04/2016
f1_keywords:
- C2692
helpviewer_keywords:
- C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
ms.openlocfilehash: 7ce57cd50e9ec83cf80ec64e14f49eb9714f9208
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177087"
---
# <a name="compiler-error-c2692"></a>编译器错误 C2692

"function_name"： C 编译器中具有 "/clr" 选项所需的完全原型的函数

在编译 .NET 托管代码时，C 编译器需要 ANSI 函数声明。 此外，如果函数不采用参数，则必须将 `void` 显式声明为参数类型。
