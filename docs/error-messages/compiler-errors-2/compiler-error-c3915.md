---
title: 编译器错误 C3915
ms.date: 11/04/2016
f1_keywords:
- C3915
helpviewer_keywords:
- C3915
ms.assetid: 2b0a5e5f-3aec-4a4b-9157-233031817084
ms.openlocfilehash: 85654e266c3157ab145e7ac7aab454a0d4f6c102
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406439"
---
# <a name="compiler-error-c3915"></a>编译器错误 C3915

type 不具有默认索引属性 （类索引器）

类型不具有默认的索引的属性。

有关详细信息，请参阅 [property](../../extensions/property-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C3915。

```
// C3915.cpp
// compile with: /clr
ref class X {
public:
// uncomment property to resolve this C3915
//   property int default[]
//   {
//      int get(int i)
//      {
//         return 863;
//      }
//   }
};

int main() {
   X^ x = new X;
   System::Console::WriteLine(x[1]);   // C3915
}
```

## <a name="example"></a>示例

如果您尝试使用默认索引器在其中使用已定义同一编译中的，也可能发生 C3915 <xref:System.Reflection.DefaultMemberAttribute>。

下面的示例生成 C3915。

```
// C3915_b.cpp
// compile with: /clr
using namespace System;

[Reflection::DefaultMember("XXX")]
ref struct A {
   property Double XXX[Double] {
      Double get(Double data) {
         return data*data;
      }
   }
};

ref struct B {
   property Double default[Double] {
      Double get(Double data) {
         return data*data;
      }
   }
};

int main() {
   A ^ mya = gcnew A();
   Console::WriteLine("{0}", mya[3]);   // C3915

   B ^ myb = gcnew B();
   Console::WriteLine("{0}", myb[3]);   // OK
}
```