---
title: 编译器错误 C3904 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3904
dev_langs:
- C++
helpviewer_keywords:
- C3904
ms.assetid: 08297605-e4f2-4c6c-b637-011f1fd40631
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4453d39b93000116b3547ff5047e6837c8d34e6a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46135967"
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