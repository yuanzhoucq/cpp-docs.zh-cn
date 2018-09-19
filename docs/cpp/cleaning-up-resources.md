---
title: 清理资源 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- termination handlers [C++], cleaning up resources
- exception handling [C++], cleaning up resources
- C++ exception handling, termination handlers
- resources [C++], cleaning up
- exception handling [C++], cleanup code
- try-catch keyword [C++], termination handlers
ms.assetid: 65753efe-6a27-4750-b90c-50635775c1b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: df75602dec8b27d12535e41b14fb2d7ca64061d1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076458"
---
# <a name="cleaning-up-resources"></a>清理资源

在终止处理程序执行期间，您在调用终止处理程序之前，可能无法知道实际分配的资源。 可能的 **__try**语句块已中断之前所分配的所有资源，以便打开并非所有资源。

因此，为安全起见，您应检查以查看哪些资源在终止处理清理之前已实际打开。 建议的过程是：

1. 将句柄初始化为 NULL。

1. 在中 **__try**语句块中，分配资源。 随着资源的分配，句柄将被设置为正值。

1. 在中 **__finally**语句块释放其对应的句柄或标志变量为非零值的每个资源或 not NULL。

## <a name="example"></a>示例

例如，以下代码使用终止处理程序关闭三个文件和在期间分配的内存块 **__try**语句块。 在清理资源之前，代码应先检查是否已分配资源。

```cpp
// exceptions_Cleaning_up_Resources.cpp
#include <stdlib.h>
#include <malloc.h>
#include <stdio.h>
#include <windows.h>

void fileOps() {
   FILE  *fp1 = NULL,
         *fp2 = NULL,
         *fp3 = NULL;
   LPVOID lpvoid = NULL;
   errno_t err;

   __try {
      lpvoid = malloc( BUFSIZ );

      err = fopen_s(&fp1, "ADDRESS.DAT", "w+" );
      err = fopen_s(&fp2, "NAMES.DAT", "w+" );
      err = fopen_s(&fp3, "CARS.DAT", "w+" );
   }
   __finally {
      if ( fp1 )
         fclose( fp1 );
      if ( fp2 )
         fclose( fp2 );
      if ( fp3 )
         fclose( fp3 );
      if ( lpvoid )
         free( lpvoid );
   }
}

int main() {
   fileOps();
}
```

## <a name="see-also"></a>请参阅

[编写终止处理程序](../cpp/writing-a-termination-handler.md)<br/>
[结构化异常处理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)