---
title: 编译器错误 C3715
ms.date: 11/04/2016
f1_keywords:
- C3715
helpviewer_keywords:
- C3715
ms.assetid: ee5dce88-ddc4-4bdb-9464-47467ce1674f
ms.openlocfilehash: c3aff142215286a94a261a1f0fcb411296b57d5a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230774"
---
# <a name="compiler-error-c3715"></a>编译器错误 C3715

"指针"：必须是指向 "class" 的指针

您在或中指定的指针 [`__hook`](../../cpp/hook.md) [`__unhook`](../../cpp/unhook.md) 不指向有效的类。 若要修复此错误，请确保 **`__hook`** 和 **`__unhook`** 调用指定指向有效类的指针。
