---
title: 编译器警告（等级1） C4488
ms.date: 11/04/2016
f1_keywords:
- C4488
helpviewer_keywords:
- C4488
ms.assetid: 55625e46-ddb5-4c7c-99c7-cd4aa9f879bd
ms.openlocfilehash: c3d176d034e679f3cca145ccb2fc77cc7fa64f3d
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965574"
---
# <a name="compiler-warning-level-1-c4488"></a>编译器警告（等级1） C4488

"function"：需要 "关键字" 关键字才能实现接口方法 "interface_method"

类必须实现它直接从中继承的接口的所有成员。 已实现的成员必须具有公共可访问性，并且必须标记为 virtual。

## <a name="example"></a>示例

如果实现的成员不是公共的，则可能会发生 C4488。 下面的示例生成 C4488。

```cpp
// C4488.cpp
// compile with: /clr /c /W1 /WX
interface struct MyI {
   void f1();
};

// implemented member not public
ref class B : MyI { virtual void f1() {} };  // C4488

// OK
ref class C : MyI {
public:
   virtual void f1() {}
};
```

## <a name="example"></a>示例

如果实现的成员未标记为 "虚拟"，则可能会发生 C4488。 下面的示例生成 C4488。

```cpp
// C4488_b.cpp
// compile with: /clr /c /W1 /WX
interface struct MyI {
   void f1();
};

ref struct B : MyI { void f1() {} };   // C4488
ref struct C : MyI { virtual void f1() {} };   // OK
```