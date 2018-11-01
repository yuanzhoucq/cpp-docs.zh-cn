---
title: 编译器警告（等级 3）C4638
ms.date: 08/27/2018
f1_keywords:
- C4638
helpviewer_keywords:
- C4638
ms.assetid: 2c07923a-e103-4e40-bd11-fdfed428a5ec
ms.openlocfilehash: 1bdd7541e16f5c02756678ae78a777094b5fe588
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651524"
---
# <a name="compiler-warning-level-3-c4638"></a>编译器警告（等级 3）C4638

> XML 文档注释目标： 引用未知符号*符号*

## <a name="remarks"></a>备注

编译器无法解析符号 (*symbol*)。 该符号在编译中必须有效。

## <a name="example"></a>示例

下面的示例生成 C4638：

```cpp
// C4638.cpp
// compile with: /clr /doc /LD /W3
using namespace System;

/// Text for class MyClass.
public ref class MyClass {
public:
   /// <summary> Text </summary>
   /// <see cref="aSymbolThatAppearsNowhereInMyProject"/>
   // Try the following line instead:
   // /// <see cref="System::Console::WriteLine"/>
   void MyMethod() {}
};   // C4638
```