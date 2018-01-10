---
title: "使用 VERIFY 代替 ASSERT |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: assert
dev_langs: C++
helpviewer_keywords:
- ASSERT statements
- debugging [MFC], ASSERT statements
- VERIFY macro
- assertions, troubleshooting ASSERT statements
- debugging assertions
- assertions, debugging
ms.assetid: 4c46397b-3fb1-49c1-a09b-41a72fae3797
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4ffe046a281bbbbefc251b48df55ecd275515e60
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="using-verify-instead-of-assert"></a>使用 VERIFY 代替 ASSERT
假设当您运行 MFC 应用程序的调试版本，没有任何问题。 但是，相同的应用程序的发行版本发生崩溃、 返回不正确的结果，和/或具有某些其他异常行为。  
  
 如果将重要代码放在一个断言语句，以验证它正常运行，则会导致此问题。 在 MFC 程序的发布版本中 ASSERT 语句注释掉，因为代码并非运行在发布版本。  
  
 如果使用断言来确认函数调用已成功，请考虑使用[验证](../../mfc/reference/diagnostic-services.md#verify)相反。 VERIFY 宏计算结果自己的自变量，在这两个调试和发行版本的应用程序。  
  
 另一项首选方法是将函数的返回值分配给临时变量，然后在 ASSERT 语句中测试该变量。  
  
 检查下面的代码片段：  
  
```  
enum {  
    sizeOfBuffer = 20  
};  
char *buf;  
ASSERT(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));  
strcpy_s( buf, sizeOfBuffer, "Hello, World" );  
free( buf );  
```  
  
 此代码在 MFC 应用程序的调试版本完全运行。 如果调用`calloc( )`失败，将显示诊断消息，其中包含的文件和行号。 但是，在零售版本的 MFC 应用程序：  
  
-   调用`calloc( )`永远不会发生，从而使`buf`未初始化，或  
  
-   `strcpy_s( )`副本"`Hello, World`"为随机段的内存，可能会损坏应用程序或导致系统停止响应，或  
  
-   `free()`尝试释放永远不会分配的内存。  
  
 若要正确使用断言，应与以下更改的代码示例：  
  
```  
enum {  
    sizeOfBuffer = 20  
};  
char *buf;  
buf = (char *) calloc(sizeOfBuffer, sizeof(char) );  
ASSERT( buf != NULL );  
strcpy_s( buf, sizeOfBuffer, "Hello, World" );  
free( buf );  
```  
  
 或者，你可以改为使用验证：  
  
```  
enum {  
    sizeOfBuffer = 20  
};  
char *buf;  
VERIFY(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));  
strcpy_s( buf, sizeOfBuffer, "Hello, World" );  
free( buf );  
```  
  
## <a name="see-also"></a>请参阅  
 [修复发行版本问题](../../build/reference/fixing-release-build-problems.md)