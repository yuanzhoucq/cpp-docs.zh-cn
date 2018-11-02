---
title: 编译器错误 C3715
ms.date: 11/04/2016
f1_keywords:
- C3715
helpviewer_keywords:
- C3715
ms.assetid: ee5dce88-ddc4-4bdb-9464-47467ce1674f
ms.openlocfilehash: 94a451bbe936507ac3b33747065a9b6aac9edd02
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660611"
---
# <a name="compiler-error-c3715"></a>编译器错误 C3715

指针： 必须是指向 class

指定在指针[__hook](../../cpp/hook.md)或[__unhook](../../cpp/unhook.md) ，未指向有效的类。 若要修复此错误，请确保你`__hook`和`__unhook`调用指定指向有效的类的指针。