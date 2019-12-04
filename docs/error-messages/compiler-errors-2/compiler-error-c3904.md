---
title: 编译器错误 C3904
ms.date: 11/04/2016
f1_keywords:
- C3904
helpviewer_keywords:
- C3904
ms.assetid: 08297605-e4f2-4c6c-b637-011f1fd40631
ms.openlocfilehash: 1861810f4598fa81d1b7662a57651b1648de1317
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749043"
---
# <a name="compiler-error-c3904"></a>编译器错误 C3904

"property_accessor"：必须指定 number 个参数

检查 `get` 中参数的数目，并对属性维度 `set` 方法。

- 对于非索引属性，`get` 方法的参数数目必须等于属性的维数或为零。

- `set` 方法的参数数目必须比属性的维数多一个。

有关详细信息，请参阅 [property](../../extensions/property-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C3904。

```cpp
// C3904.cpp
// compile with: /clr /c
ref class X {
   property int P {
      // set
      void set();   // C3904
      // try the following line instead
      // void set(int);

      // get
      int get(int, int);   // C3904
      // try the following line instead
      // int get();
   };
};
```

## <a name="example"></a>示例

下面的示例生成 C3904。

```cpp
// C3904b.cpp
// compile with: /clr /c
ref struct X {
   property int Q[double, double, float, float, void*, int] {
      // set
      void set(double, void*);   // C3904
      // try the following line instead
      // void set(double, double, float, float, void*, int, int);

      // get
      int get();   // C3904
      // try the following line instead
      // int get(double, double, float, float, void*, int);
   }
};
```
