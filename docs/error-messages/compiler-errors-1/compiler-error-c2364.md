---
title: 编译器错误 C2364
ms.date: 11/04/2016
f1_keywords:
- C2364
helpviewer_keywords:
- C2364
ms.assetid: 4f550571-94b5-42ca-84cb-663fecbead44
ms.openlocfilehash: 051468ea861190dd3f6a28dc272f1bab155145af
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558894"
---
# <a name="compiler-error-c2364"></a>编译器错误 C2364

type： 自定义特性的非法类型

自定义特性的命名的参数被限制为编译时常量。 例如，整数类型 （int、 char 等），system:: type ^，和 system:: object ^。

## <a name="example"></a>示例

下面的示例生成 C2364。

```
// c2364.cpp
// compile with: /clr /c
using namespace System;

[attribute(AttributeTargets::All)]
public ref struct ABC {
public:
   // Delete the following line to resolve.
   ABC( Enum^ ) {}   // C2364
   ABC( int ) {}   // OK
};
```