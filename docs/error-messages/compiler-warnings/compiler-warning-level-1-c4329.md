---
title: 编译器警告（等级 1）C4329
ms.date: 11/04/2016
f1_keywords:
- C4329
helpviewer_keywords:
- C4329
ms.assetid: 4316f51a-2c56-4b3f-831e-65d24b83b65c
ms.openlocfilehash: 31ea3aec2c7dd8e02a23a5c3cf6e5ac406636516
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390511"
---
# <a name="compiler-warning-level-1-c4329"></a>编译器警告（等级 1）C4329

__declspec(align()) is ignored on enum

利用[对齐](../../cpp/align-cpp.md)关键字[__declspec](../../cpp/declspec.md)上不允许使用修饰符`enum`。 下面的示例生成 C4329:

```
// C4329.cpp
// compile with: /W1 /LD
enum __declspec(align(256)) TestEnum {   // C4329
   TESTVAL1,
   TESTVAL2,
   TESTVAL3
};
__declspec(align(256)) enum TestEnum1;
```