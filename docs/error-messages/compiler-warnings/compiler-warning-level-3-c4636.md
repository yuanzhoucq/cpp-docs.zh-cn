---
title: 编译器警告 （等级 3） C4636 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4636
dev_langs:
- C++
helpviewer_keywords:
- C4636
ms.assetid: 59112a0f-850f-41c6-bd84-8ae8dc84706a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cf7dd13e4df2e07df362c04763125dd7954c986b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113664"
---
# <a name="compiler-warning-level-3-c4636"></a>编译器警告（等级 3）C4636

应用于“construct”: 标记的 XML 文档注释需要非空 '' 特性。

标记（如 `cref`）没有值。

## <a name="example"></a>示例

以下示例生成 C4636。

```
// C4636.cpp
// compile with: /clr /doc /W3 /c
/// <see cref=''/>
// /// <see cref='System::Exception'/>
ref struct A {   // C4636
   void f(int);
};

// OK
/// <see cref='System::Exception'/>
ref struct B {
   void f(int);
};
```