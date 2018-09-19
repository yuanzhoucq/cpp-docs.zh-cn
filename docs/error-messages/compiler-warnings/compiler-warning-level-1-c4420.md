---
title: 编译器警告 （等级 1） C4420 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4420
dev_langs:
- C++
helpviewer_keywords:
- C4420
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1ba4ef4c4fc006e1a5950d0d16dc530ccc06a1d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049743"
---
# <a name="compiler-warning-level-1-c4420"></a>编译器警告（等级 1）C4420

operator： 运算符不可用，改用 operator;运行时检查可能会危及

当你使用时，会生成此警告[/RTCv](../../build/reference/rtc-run-time-error-checks.md) （矢量检查新/删除），并且当找到没有向量形式。 在这种情况下，使用非向量窗体。

为了使 /RTCv 才能正常工作，编译器应始终调用的向量形式[新](../../cpp/new-operator-cpp.md)/[删除](../../cpp/delete-operator-cpp.md)如果时使用的矢量语法。