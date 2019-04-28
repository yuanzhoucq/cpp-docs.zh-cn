---
title: 编译器警告（等级 1）C4229
ms.date: 11/04/2016
f1_keywords:
- C4229
helpviewer_keywords:
- C4229
ms.assetid: aadfc83b-1e5f-4229-bd0a-9c10a5d13182
ms.openlocfilehash: 05d11a02d3aea8748a2955dff77a0af750ee0275
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207496"
---
# <a name="compiler-warning-level-1-c4229"></a>编译器警告（等级 1）C4229

使用了记时错误： 在数据上的修饰符将被忽略

使用 Microsoft 修饰符，如`__cdecl`过时的做法是在数据声明。

## <a name="example"></a>示例

```
// C4229.cpp
// compile with: /W1 /LD
int __cdecl counter;   // C4229 cdecl ignored
```