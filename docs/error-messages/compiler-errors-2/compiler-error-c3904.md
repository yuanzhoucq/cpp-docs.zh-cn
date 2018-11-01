---
title: 编译器错误 C3904
ms.date: 11/04/2016
f1_keywords:
- C3904
helpviewer_keywords:
- C3904
ms.assetid: 08297605-e4f2-4c6c-b637-011f1fd40631
ms.openlocfilehash: 8c7f4a2861825a35d676328b5e283a5e4087d85b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519777"
---
# <a name="compiler-error-c3904"></a>编译器错误 C3904

property_accessor： 必须指定数字参数

检查中的参数数量你`get`和`set`方法针对属性维度。

- 参数数目`get`方法必须等于的维度的属性的数量或为零的非索引属性。

- 参数的数目`set`方法必须是一个多个维度的属性的数目。

有关详细信息，请参阅 [property](../../windows/property-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C3904。

```
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

```
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