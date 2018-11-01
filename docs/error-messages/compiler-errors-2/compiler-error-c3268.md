---
title: 编译器错误 C3268
ms.date: 11/04/2016
f1_keywords:
- C3268
helpviewer_keywords:
- C3268
ms.assetid: d74a630c-daea-4e29-9759-83efef7fb184
ms.openlocfilehash: c766488b29273f321feffa8e38a97e54454db7b1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480530"
---
# <a name="compiler-error-c3268"></a>编译器错误 C3268

> '*函数*： 泛型函数或泛型类的成员函数不能具有变量参数列表

## <a name="remarks"></a>备注

**/Clr: pure**并 **/clr: safe**编译器选项在 Visual Studio 2015 中弃用，在 Visual Studio 2017 中不受支持。

请参阅[泛型](../../windows/generics-cpp-component-extensions.md)有关详细信息。

## <a name="example"></a>示例

以下示例生成 C3268。

```cpp
// C3268.cpp
// compile with: /clr:pure /c
generic <class ItemType>
void Test(ItemType item, ...) {}   // C3268
// try the following line instead
// void Test(ItemType item) {}

generic <class ItemType2>
ref struct MyStruct { void Test(...){} };   // C3268
// try the following line instead
// ref struct MyStruct { void Test2(){} };   // OK
```