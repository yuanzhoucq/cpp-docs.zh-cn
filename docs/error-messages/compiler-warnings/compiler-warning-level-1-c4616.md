---
title: 编译器警告（等级 1）C4616
ms.date: 11/04/2016
f1_keywords:
- C4616
helpviewer_keywords:
- C4616
ms.assetid: 71e15265-c5bc-42ce-a6a9-4879892472b1
ms.openlocfilehash: fd36d0cdbcaaeca4f84ce85aa80f3bb1fba616a0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185901"
---
# <a name="compiler-warning-level-1-c4616"></a>编译器警告（等级 1）C4616

\#pragma warning：警告编号 "number" 不是有效的编译器警告

不能重新分配在[警告](../../preprocessor/warning.md)杂注中指定的警告编号。 已忽略杂注。

下面的示例生成 C4616：

```cpp
// C4616.cpp
// compile with: /W1 /c
#pragma warning( disable : 0 )   // C4616
#pragma warning( disable : 999 )   // OK
#pragma warning( disable : 4998 )   // OK
```
