---
title: 程序终止中的 return 语句 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], function return types
- function return types [C++], return statement
- return keyword [C++], syntax
ms.assetid: 66d002ab-5625-4b68-8446-71e1b8fcdbd8
ms.openlocfilehash: 9c7b6130ee1a0b49ab75a70d84764d3a1f8c5ef0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613039"
---
# <a name="return-statement-in-program-termination-c"></a>程序终止中的 return 语句 (C++)

发出**返回**从语句`main`在功能上等效于调用`exit`函数。 请看下面的示例：

```cpp
// return_statement.cpp
#include <stdlib.h>
int main()
{
    exit( 3 );
    return 3;
}
```

`exit`并**返回**中前面的示例中的语句是功能上相同。 但是，c + + 需要具有的函数而不返回类型**void**返回值。 **返回**语句可以返回一个介于`main`。

## <a name="see-also"></a>请参阅

[程序终止](../cpp/program-termination.md)