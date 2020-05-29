---
title: 编译器错误 C2144
ms.date: 11/04/2016
f1_keywords:
- C2144
helpviewer_keywords:
- C2144
ms.assetid: 49f3959b-324f-4c06-9588-c0ecef5dc5b3
ms.openlocfilehash: b917c0a2c15aeb70222c948bce9a6fb275c91068
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80207241"
---
# <a name="compiler-error-c2144"></a>编译器错误 C2144

> 语法错误： "*type*" 前面应为 "*token*"

编译器需要*标记*，而应找到*类型*。

此错误可能由缺少右大括号、右括号或分号引起。

尝试从包含空格字符的 CLR 关键字创建宏时也可能会发生 C2144。

如果尝试进行类型转发，还可能会看到 C2144。 有关详细信息，请参阅[类型转发（C++/cli）](../../extensions/type-forwarding-cpp-cli.md) 。

## <a name="examples"></a>示例

下面的示例生成 C2144，并演示如何修复此问题：

```cpp
// C2144.cpp
// compile with: /clr /c
#define REF ref
REF struct MyStruct0;   // C2144

// OK
#define REF1 ref struct
REF1 MyStruct1;
```

下面的示例生成 C2144，并演示如何修复此问题：

```cpp
// C2144_2.cpp
// compile with: /clr /c
ref struct X {

   property double MultiDimProp[,,] {   // C2144
   // try the following line instead
   // property double MultiDimProp[int , int, int] {
      double get(int, int, int) { return 1; }
      void set(int i, int j, int k, double l) {}
   }

   property double MultiDimProp2[] {   // C2144
   // try the following line instead
   // property double MultiDimProp2[int] {
      double get(int) { return 1; }
      void set(int i, double l) {}
   }
};
```
