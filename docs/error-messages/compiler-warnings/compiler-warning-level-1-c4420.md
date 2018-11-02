---
title: 编译器警告（等级 1）C4420
ms.date: 11/04/2016
f1_keywords:
- C4420
helpviewer_keywords:
- C4420
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
ms.openlocfilehash: a4a7e91e7845cc0fc25d5a6fad16ae7b7e327952
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662880"
---
# <a name="compiler-warning-level-1-c4420"></a>编译器警告（等级 1）C4420

operator： 运算符不可用，改用 operator;运行时检查可能会危及

当你使用时，会生成此警告[/RTCv](../../build/reference/rtc-run-time-error-checks.md) （矢量检查新/删除），并且当找到没有向量形式。 在这种情况下，使用非向量窗体。

为了使 /RTCv 才能正常工作，编译器应始终调用的向量形式[新](../../cpp/new-operator-cpp.md)/[删除](../../cpp/delete-operator-cpp.md)如果时使用的矢量语法。