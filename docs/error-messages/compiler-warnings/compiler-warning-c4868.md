---
title: 编译器警告 C4868
ms.date: 10/26/2017
f1_keywords:
- C4868
ms.assetid: fc6aa7e5-34dd-4ec2-88bd-16e430361dc7
ms.openlocfilehash: d0bc8716e53e71c52f6a31036a95d0b4cefedd79
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481312"
---
# <a name="compiler-warning-level-4-c4868"></a>编译器警告 （等级 C4868

> '_文件_(*line_number*) 编译器不会强制在大括号内的初始值设定项列表中的从左到右计算顺序

大括号内的初始值设定项列表的元素将按从左到右顺序计算。 有两种情况下，在其中，编译器不能以保证此顺序： 第一个是对象的值; 传递时的一些元素第二个是编译时`/clr`和的某些元素是字段的对象或数组元素。 当编译器无法保证从左到右评估时它会发出警告 C4868。

已经为 Visual c + + 2015 Update 2 的编译器一致性工作可以生成此警告。 在 Visual c + + 2015 Update 2 之前已编译的代码现在可以生成 C4868。

默认情况下，此警告处于关闭状态。 使用`/Wall`来激活此警告。

若要解决此警告，首先要考虑的初始值设定项列表元素的从左到右评估是否是必需的例如当元素的评估可能会生成依赖于顺序的副作用。 在许多情况下，元素的计算顺序没有明显的影响。

如果求值的顺序必须是从左到右，请考虑是否可以传递元素`const`改为引用。 此更改消除了下面的代码示例中的警告。

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