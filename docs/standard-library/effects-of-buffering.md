---
title: "缓冲效果 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- buffers, effects of buffering
- buffering, effects of
ms.assetid: 5d544812-e95e-4f28-b15a-edef3f3414fd
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: d888b6d16e0a71168e0615d89bbd1d03c51afad8
ms.lasthandoff: 02/24/2017

---
# <a name="effects-of-buffering"></a>缓冲效果
下面的示例演示缓冲的效果。 可使程序打印 `please wait`、等待 5 秒然后继续。 但是由于输已缓冲，所以这不一定有效。  
  
```  
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
  
```  
cout <<"Please wait..." <<flush;  
```  
  
 此步骤将刷新缓冲区，确保在等待之前输出消息。 还可以使用 `endl` 操控器刷新缓冲区并输出回车符-换行符，也可以使用 `cin` 对象。 此对象（与 `cerr` 或 `clog` 对象一起）通常绑定到 `cout` 对象。 因此，对 `cin` （或 `cerr` 或 `clog` 对象）的任何使用将刷新 `cout` 对象。  
  
## <a name="see-also"></a>另请参阅  
 [输出流](../standard-library/output-streams.md)


