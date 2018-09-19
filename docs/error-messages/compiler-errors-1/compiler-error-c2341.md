---
title: 编译器错误 C2341 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2341
dev_langs:
- C++
helpviewer_keywords:
- C2341
ms.assetid: aa2a7da5-e1c8-4225-9939-5bdc50158f31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: adac1e6f6e5f5d58b6091a389537a42f0e496b31
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020194"
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