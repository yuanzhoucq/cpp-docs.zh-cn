---
title: 编译器警告（等级 3）C4359
ms.date: 11/04/2016
f1_keywords:
- C4359
helpviewer_keywords:
- C4359
ms.assetid: d8fe993c-ef82-45a0-a43d-c29f9d1bacdb
ms.openlocfilehash: 3856c50aabce497f28a179b30346b30371986e51
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432807"
---
# <a name="compiler-warning-level-3-c4359"></a>编译器警告（等级 3）C4359

type： 实际对齐方式 (8) 是大于 __declspec(align()) 中指定的值

指定类型的对齐方式小于一个数据成员的类型的对齐方式。  有关详细信息，请参阅[对齐](../../cpp/align-cpp.md)。

## <a name="example"></a>示例

下面的示例生成 C4359。

```
// C4359.cpp
// compile with: /W3 /c
struct __declspec(align(8)) C8 { __int64 i; };
struct __declspec(align(4)) C4  { C8 m8; };   // C4359
struct __declspec(align(8)) C8_b  { C8 m8; };   // OK
struct __declspec(align(16)) C16  { C8 m8; };   // OK
```