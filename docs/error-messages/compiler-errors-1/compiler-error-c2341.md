---
title: 编译器错误 C2341
ms.date: 11/04/2016
f1_keywords:
- C2341
helpviewer_keywords:
- C2341
ms.assetid: aa2a7da5-e1c8-4225-9939-5bdc50158f31
ms.openlocfilehash: 4356182758398fa7ed1ec6a069affa4bb99ace1a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188214"
---
# <a name="compiler-error-c2341"></a>编译器错误 C2341

section name： 必须使用 #pragma data_seg、 code_seg 或部分之前，若要使用定义段

[分配](../../cpp/allocate.md)语句引用尚未定义的某个段[code_seg](../../preprocessor/code-seg.md)， [data_seg](../../preprocessor/data-seg.md)，或者[部分](../../preprocessor/section.md)杂注。

下面的示例生成 C2341:

```
// C2341.cpp
// compile with: /c
__declspec(allocate(".test"))   // C2341
int j = 1;
```

可能的解决方法：

```
// C2341b.cpp
// compile with: /c
#pragma data_seg(".test")
__declspec(allocate(".test"))
int j = 1;
```