---
title: 编译器错误 C2599 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2599
dev_langs:
- C++
helpviewer_keywords:
- C2599
ms.assetid: 88515f36-7589-47e2-862e-0de8b18d6668
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 515e380ea87b8ea648a00644ce8bca6428903f18
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044478"
---
# <a name="compiler-error-c2599"></a>编译器错误 C2599

enum： 不允许前向声明枚举类型

编译器不再支持前向声明托管枚举。

前向声明枚举类型，不允许在[/Za](../../build/reference/za-ze-disable-language-extensions.md)。

下面的示例生成 C2599:

```
// C2599.cpp
// compile with: /clr /c
enum class Status;   // C2599

enum class Status2 { stop2, hold2, go2};

ref struct MyStruct {
   // Delete the following line to resolve.
   Status m_status;

   Status2 m_status2;   // OK
};

enum class Status { stop, hold, go };
```