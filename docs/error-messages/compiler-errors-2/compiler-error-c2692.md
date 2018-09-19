---
title: 编译器错误 C2692 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2692
dev_langs:
- C++
helpviewer_keywords:
- C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 03a9006889c5853e77b5603484ea9d18f2474241
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088366"
---
# <a name="compiler-error-c2692"></a>编译器错误 C2692

function_name： 完全原型的函数中使用的 C 编译器需要 / clr 选项

编译.NET 托管代码时，C 编译器需要 ANSI 函数声明。 此外，如果函数没有任何参数，它必须显式声明`void`作为参数类型。