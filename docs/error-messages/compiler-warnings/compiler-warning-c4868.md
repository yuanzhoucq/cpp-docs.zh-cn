---
title: 编译器警告 C4868 |Microsoft 文档
ms.date: 10/26/2017
ms.topic: error-reference
f1_keywords:
- C4868
ms.assetid: fc6aa7e5-34dd-4ec2-88bd-16e430361dc7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 922a1a8434da8449758b9d55ebe89ace2f262cd5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4868"></a>编译器警告 （等级 4） C4868

> _文件_(*line_number*) 编译器可能会不强制实施大括号内的初始值设定项列表中从左到右计算顺序

大括号内的初始值设定项列表中的元素是从左到右的顺序进行计算。 有两种情况下，编译器处于无法保证此顺序： 第一种是通过值; 传递的对象时的某些元素第二个是编译时`/clr`和的某些元素的对象的字段或数组元素。 当编译器无法保证从左到右评估它会发出警告 C4868。

于为 Visual c + + 2015 Update 2 执行的编译器一致性工作可以生成此警告。 Visual c + + 2015 Update 2 之前的版本编译的代码现在可以生成 C4868。

默认情况下，此警告处于关闭状态。 使用`/Wall`来激活此警告。

若要解决此警告，首先考虑的初始值设定项列表元素的从左到右评估是否是必需的如元素的求值时可能会产生顺序相关的副作用。 在许多情况下，在其中计算元素的顺序没有明显的影响。

如果求值的顺序必须是从左到右，请考虑它是否可以传入元素`const`改为引用。 此更改消除了下面的代码示例中的警告。

## <a name="example"></a>示例

此示例生成 C4868，并显示了如何修复此错误：

```cpp
// C4868.cpp
// compile with: /c /Wall
#include <cstdio>

class HasCopyConstructor
{
public:
    int x;

    HasCopyConstructor(int x): x(x) {}

    HasCopyConstructor(const HasCopyConstructor& h): x(h.x)
    {
        printf("Constructing %d\n", h.x);
    }
};

class TripWarning4868
{
public:
    // note that taking "HasCopyConstructor" parameters by-value will trigger copy-construction.
    TripWarning4868(HasCopyConstructor a, HasCopyConstructor b) {}

    // This variation will not trigger the warning:
    // TripWarning4868(const HasCopyConstructor& a, const HasCopyConstructor& b) {}
};

int main()
{
    HasCopyConstructor a{1};
    HasCopyConstructor b{2};

    // the warning will indicate the below line, the usage of the braced initializer list.
    TripWarning4868 warningOnThisLine{a, b};
};
```