---
title: return 语句在程序终止 （C++） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- data types [C++], function return types
- function return types [C++], return statement
- return keyword [C++], syntax
ms.assetid: 66d002ab-5625-4b68-8446-71e1b8fcdbd8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cfcf65258767178c0f74f63ca6e938e1d940e3be
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061131"
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