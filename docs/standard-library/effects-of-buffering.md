---
title: 缓冲效果
ms.date: 11/04/2016
helpviewer_keywords:
- buffers, effects of buffering
- buffering, effects of
ms.assetid: 5d544812-e95e-4f28-b15a-edef3f3414fd
ms.openlocfilehash: 1f28748f1e7a837ad87ef1cfcebc56d3410d0fd2
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458913"
---
# <a name="effects-of-buffering"></a>缓冲效果

下面的示例演示缓冲的效果。 可使程序打印 `please wait`、等待 5 秒然后继续。 但是由于输已缓冲，所以这不一定有效。

```cpp
// effects_buffering.cpp
// compile with: /EHsc
#include <iostream>
#include <time.h>
using namespace std;

int main( )
{
   time_t tm = time( NULL ) + 5;
   cout << "Please wait...";
   while ( time( NULL ) < tm )
      ;
   cout << "\nAll done" << endl;
}
```

要使程序有逻辑地工作，将要显示消息时， `cout` 对象自身必须为空。 若要刷新 `ostream` 对象，请将其发送至 `flush` 操控器：

```cpp
cout <<"Please wait..." <<flush;
```

此步骤将刷新缓冲区，确保在等待之前输出消息。 你还可以使用`endl`操控器, 该操控器刷新缓冲区并输出一个回车行源, 或者可以`cin`使用对象。 此对象（与 `cerr` 或 `clog` 对象一起）通常绑定到 `cout` 对象。 因此，对 `cin` （或 `cerr` 或 `clog` 对象）的任何使用将刷新 `cout` 对象。

## <a name="see-also"></a>请参阅

[输出流](../standard-library/output-streams.md)
