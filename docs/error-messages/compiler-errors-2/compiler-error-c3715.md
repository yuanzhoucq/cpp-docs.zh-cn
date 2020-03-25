---
title: 编译器错误 C3715
ms.date: 11/04/2016
f1_keywords:
- C3715
helpviewer_keywords:
- C3715
ms.assetid: ee5dce88-ddc4-4bdb-9464-47467ce1674f
ms.openlocfilehash: 13befc17b94fdf2c22cb84bc64ed55b9375b3473
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165907"
---
# <a name="compiler-error-c3715"></a>编译器错误 C3715

"指针"：必须是指向 "class" 的指针

在[__hook](../../cpp/hook.md)或[__unhook](../../cpp/unhook.md)中指定的指针不指向有效的类。 若要修复此错误，请确保 `__hook` 和 `__unhook` 调用指定指向有效类的指针。
