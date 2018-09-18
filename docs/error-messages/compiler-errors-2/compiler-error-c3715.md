---
title: 编译器错误 C3715 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3715
dev_langs:
- C++
helpviewer_keywords:
- C3715
ms.assetid: ee5dce88-ddc4-4bdb-9464-47467ce1674f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 63ae3486b4db21a3aa241d5ebdbbfa0cdc6806f2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026551"
---
# <a name="compiler-error-c3715"></a>编译器错误 C3715

指针： 必须是指向 class

指定在指针[__hook](../../cpp/hook.md)或[__unhook](../../cpp/unhook.md) ，未指向有效的类。 若要修复此错误，请确保你`__hook`和`__unhook`调用指定指向有效的类的指针。