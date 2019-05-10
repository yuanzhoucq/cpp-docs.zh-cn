---
title: 编译器警告（等级 1）C4305
ms.date: 1/17/2018
f1_keywords:
- C4305
helpviewer_keywords:
- C4305
ms.openlocfilehash: 3f9116b0e7bdd9ee13c42b48f44da4b090f41ccd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327465"
---
# <a name="compiler-warning-level-1-c4305"></a>编译器警告（等级 1）C4305

> '*上下文*： 从截断*type1*to*type2*

## <a name="remarks"></a>备注

一个值转换为较小的类型进行初始化，或作为构造函数参数，从而导致信息丢失时，将发出此警告。

## <a name="example"></a>示例

以下示例显示两种方法可能会看到此警告：

```cpp
// C4305.cpp
// Compile by using: cl /EHsc /W4 C4305.cpp

struct item
{
    item(float) {}
};

int main()
{
    float f = 2.71828;          // C4305 'initializing'
    item i(3.14159);            // C4305 'argument'
    return static_cast<int>(f);
}
```

若要解决此问题，请使用正确类型的值初始化或使用显式强制转换为正确的类型。 例如，使用**float** 2.71828f 而不是如文字**double** （浮点文本默认类型） 来初始化**float**变量，或要传递给构造函数采用**float**参数。
