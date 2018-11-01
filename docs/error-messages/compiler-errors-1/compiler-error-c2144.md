---
title: 编译器错误 C2144
ms.date: 11/04/2016
f1_keywords:
- C2144
helpviewer_keywords:
- C2144
ms.assetid: 49f3959b-324f-4c06-9588-c0ecef5dc5b3
ms.openlocfilehash: f6472fc70ee4a86bed1422941e758127009f14cb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483325"
---
# <a name="compiler-error-c2144"></a>编译器错误 C2144

> 语法错误: '*类型*之前应该是*令牌*

编译器预期*令牌*并找到*类型*相反。

缺少右大括号、 右圆括号或分号可能导致此错误。

尝试从包含空白字符的 CLR 关键字创建宏时，也会发生 C2144。

如果你尝试进行类型转发，还可能会看到 C2144。 请参阅[类型转发 (C + + CLI)](../../windows/type-forwarding-cpp-cli.md)有关详细信息。

## <a name="examples"></a>示例

下面的示例生成 C2144，并显示了如何修复此错误：

```cpp
// C2144.cpp
// compile with: /clr /c
#define REF ref
REF struct MyStruct0;   // C2144

// OK
#define REF1 ref struct
REF1 MyStruct1;
```

下面的示例生成 C2144，并显示了如何修复此错误：

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