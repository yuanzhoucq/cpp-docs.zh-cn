---
title: 编译器错误 C2937 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2937
dev_langs:
- C++
helpviewer_keywords:
- C2937
ms.assetid: 95671ca3-79f7-4b56-a5f2-a92296da1629
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ccb13a7cf95e1f63bd10b3901a3c2157a7fe29bf
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061784"
---
# <a name="compiler-error-c2937"></a>编译器错误 C2937

“class”：type-class-id 被重新定义为全局 typedef

不能将泛型或模板类用作全局 `typedef`成员。

下面的示例生成 C2937：

```
// C2937.cpp
// compile with: /c
template<class T>
struct TC { };
typedef int TC<int>;   // C2937
typedef TC<int> c;   // OK
```

使用泛型时，也可能发生 C2937：

```
// C2937b.cpp
// compile with: /clr
generic<class T>
ref struct GC { };
typedef int GC<int>;   // C2937
typedef GC<int> xx;   // OK
```