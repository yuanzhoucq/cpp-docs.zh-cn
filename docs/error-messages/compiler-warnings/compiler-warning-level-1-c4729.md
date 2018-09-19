---
title: 编译器警告 （等级等级 1)c4729 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4729
dev_langs:
- C++
helpviewer_keywords:
- C4729
ms.assetid: 36a0151f-f258-48d9-9444-ae6d41ff70a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7d1f5b4fe452937ce74e56886a5214ff92f44af7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096075"
---
# <a name="compiler-warning-level-1-c4729"></a>编译器警告（等级 1）C4729

根据警告，函数对于流图形太大

当函数太大，不能用可靠的方法（如检查是否有将生成警告的情况）进行编译时生成此警告。 仅在使用 [/Od](../../build/reference/od-disable-debug.md) 编译器选项时生成此警告。

若要解决此警告，请将函数拆成较小的函数。