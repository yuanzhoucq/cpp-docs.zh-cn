---
title: 编译器错误 C2692
ms.date: 11/04/2016
f1_keywords:
- C2692
helpviewer_keywords:
- C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
ms.openlocfilehash: c469f4944417c9116c7316b01642dd4b370b8c4b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611154"
---
# <a name="compiler-error-c2692"></a>编译器错误 C2692

function_name： 完全原型的函数中使用的 C 编译器需要 / clr 选项

编译.NET 托管代码时，C 编译器需要 ANSI 函数声明。 此外，如果函数没有任何参数，它必须显式声明`void`作为参数类型。