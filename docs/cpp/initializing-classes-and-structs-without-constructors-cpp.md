---
title: 在没有构造函数的情况下初始化类和结构 (C++)
ms.date: 10/17/2018
ms.assetid: 3e55c3d6-1c6b-4084-b9e5-221b151402f4
ms.openlocfilehash: 4f696f4fc8862b953e40a03c96b88d1a0b7f720b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547324"
---
# <a name="initializing-classes-and-structs-without-constructors-c"></a>在没有构造函数的情况下初始化类和结构 (C++)

并不总是需要为类定义构造函数，特别是相对比较简单的类。 用户可以使用统一初始化来初始化类或结构的对象，如下面的示例所示：

```cpp
// no_constructor.cpp
// Compile with: cl /EHsc no_constructor.cpp
#include <time.h>

// No constructor
struct TempData
{
    int StationId;
    time_t timeSet;
    double current;
    double maxTemp;
    double minTemp;
};

// Has a constructor
struct TempData2
{
    TempData2(double minimum, double maximum, double cur, int id, time_t t) :
       stationId{id}, timeSet{t}, current{cur}, maxTemp{maximum}, minTemp{minimum} {}
    int stationId;
    time_t timeSet;
    double current;
    double maxTemp;
    double minTemp;
};

int main()
{
    time_t time_to_set;

    // Member initialization (in order of declaration):
    TempData td{ 45978, time(&time_to_set), 28.9, 37.0, 16.7 };

    // Default initialization = {0,0,0,0,0}
    TempData td_default{};

    // Uninitialized = if used, emits warning C4700 uninitialized local variable
    TempData td_noInit;

    // Member declaration (in order of ctor parameters)
    TempData2 td2{ 16.7, 37.0, 28.9, 45978, time(&time_to_set) };

    return 0;
}
```

请注意，当类或结构具有没有构造函数，您提供将成员声明的类中的顺序列表元素。 如果类具有构造函数，提供按参数顺序的元素。

## <a name="see-also"></a>请参阅

[类和结构](../cpp/classes-and-structs-cpp.md)<br/>
[构造函数](../cpp/constructors-cpp.md)
