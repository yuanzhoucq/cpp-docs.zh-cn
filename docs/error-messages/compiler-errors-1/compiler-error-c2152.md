---
title: 编译器错误 C2152 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2152
dev_langs:
- C++
helpviewer_keywords:
- C2152
ms.assetid: a9ea2b0c-d55d-41c7-ba9f-dd75592ffc8a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b3a2215e43573b08a69501edfbd0c7c86897fdd3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064890"
---
# <a name="compiler-error-c2152"></a>编译器错误 C2152

identifier： 指向具有不同的属性的函数的指针

指向具有一个调用约定的函数的指针 (`__cdecl`， `__stdcall`，或`__fastcall`) 分配给到具有另一个调用约定的函数指针。