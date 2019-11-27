---
title: 编译器警告（等级 4）C4239
ms.date: 11/04/2016
f1_keywords:
- C4239
helpviewer_keywords:
- C4239
ms.assetid: a23dc16a-649e-4870-9a24-275de1584fcd
ms.openlocfilehash: fcb66fca7e5b8708171849f885518c15b8355ac4
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541734"
---
# <a name="compiler-warning-level-4-c4239"></a>编译器警告（等级 4）C4239

使用了非标准扩展： "token"：从 "type" 转换为 "type"

C++标准不允许此类型转换，但此处允许它作为扩展。 此警告后面紧跟至少一个说明违反语言规则的说明。

## <a name="example"></a>示例

下面的示例生成 C4239。

```cpp
// C4239.cpp
// compile with: /W4 /c
struct C {
   C() {}
};

void func(void) {
   C & rC = C();   // C4239
   const C & rC2 = C();   // OK
   rC2;
}
```

## <a name="example"></a>示例

不严格允许从整型转换为枚举类型。

下面的示例生成 C4239。

```cpp
// C4239b.cpp
// compile with: /W4 /c
enum E { value };
struct S {
   E e : 2;
} s = { 5 };   // C4239
// try the following line instead
// } s = { (E)5 };
```