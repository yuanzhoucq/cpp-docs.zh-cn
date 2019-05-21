---
title: 如何：声明固定指针和值类型
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- value types, declaring
- pinning pointers
ms.assetid: 57c5ec8a-f85a-48c4-ba8b-a81268bcede0
ms.openlocfilehash: 901980c76aac5dd364f2fa2fae0e007f5d25f3d8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515732"
---
# <a name="how-to-declare-pinning-pointers-and-value-types"></a>如何：声明固定指针和值类型

值类型可以隐式装箱。 然后，可以声明指向值类型本身的固定指针，并使用指向装箱值类型 pin_ptr。

## <a name="example"></a>示例

### <a name="code"></a>代码

```cpp
// pin_ptr_value.cpp
// compile with: /clr
value struct V {
   int i;
};

int main() {
   V ^ v = gcnew V;   // imnplicit boxing
   v->i=8;
   System::Console::WriteLine(v->i);
   pin_ptr<V> mv = &*v;
   mv->i = 7;
   System::Console::WriteLine(v->i);
   System::Console::WriteLine(mv->i);
}
```

```Output
8
7
7
```

## <a name="see-also"></a>请参阅

[pin_ptr (C++/CLI)](pin-ptr-cpp-cli.md)