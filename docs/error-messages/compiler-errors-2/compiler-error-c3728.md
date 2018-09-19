---
title: 编译器错误 C3728 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3728
dev_langs:
- C++
helpviewer_keywords:
- C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e412824bd2afdadfc21d71b73f38eb8ba5ace82d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108412"
---
# <a name="compiler-error-c3728"></a>编译器错误 C3728

event： 事件没有引发方法

使用的语言创建的元数据，如 C# 中，不允许在其中定义的该类的外部引发的事件，是随[#using](../../preprocessor/hash-using-directive-cpp.md)指令和使用尝试的 CLR 编程的 Visual c + + 程序引发事件。

若要将提升在 C# 等语言中开发的程序中的事件，包含该事件的类需要还定义一个引发事件的公共方法。