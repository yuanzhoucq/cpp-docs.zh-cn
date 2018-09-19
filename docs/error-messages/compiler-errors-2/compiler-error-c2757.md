---
title: 编译器错误 C2757 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2757
dev_langs:
- C++
helpviewer_keywords:
- C2757
ms.assetid: 421f102f-8a32-4d47-a109-811ddf2c909d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ff853ad499a9d50cc1c5c168ac13a570453dcba
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057998"
---
# <a name="compiler-error-c2757"></a>编译器错误 C2757

symbol： 具有此名称的符号已存在，因此此名称不能用作命名空间名称

中引用的程序集中已使用的命名空间标识符作为当前编译中使用的符号。

下面的示例生成 C2757:

```
// C2757a.cpp
// compile with: /clr /LD
public ref class Nes {};
```

然后，

```
// C2757b.cpp
// compile with: /clr /c
#using <C2757a.dll>

namespace Nes {    // C2757
// try the following line instead
// namespace Nes2 {
   public ref class X {};
}
```
