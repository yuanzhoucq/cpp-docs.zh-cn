---
title: 编译器警告（等级 1）C4420
ms.date: 11/04/2016
f1_keywords:
- C4420
helpviewer_keywords:
- C4420
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
ms.openlocfilehash: 72ab87b34e07717112f5af1727a216b4f786ae0d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186785"
---
# <a name="compiler-warning-level-1-c4420"></a>编译器警告（等级 1）C4420

"operator"：运算符不可用，请改用 "operator";可能会危及运行时检查

当你使用[/RTCv](../../build/reference/rtc-run-time-error-checks.md) （矢量新建/删除检查）和未找到矢量窗体时，将生成此警告。 在这种情况下，将使用非向量窗体。

若要使/RTCv 正常工作，如果使用向量语法，编译器应始终调用[new](../../cpp/new-operator-cpp.md)/[delete](../../cpp/delete-operator-cpp.md)的矢量形式。
