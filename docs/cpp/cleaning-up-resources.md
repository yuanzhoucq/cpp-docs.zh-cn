---
title: "清理资源 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ 异常处理, 终止处理程序"
  - "异常处理, 清理资源"
  - "异常处理, 清理代码"
  - "资源 [C++], 清理"
  - "终止处理程序, 清理资源"
  - "try-catch 关键字 [C++], 终止处理程序"
ms.assetid: 65753efe-6a27-4750-b90c-50635775c1b6
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 清理资源
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在终止处理程序执行期间，您在调用终止处理程序之前，可能无法知道实际分配的资源。  `__try` 语句块可能会在所有资源被分配之前中断，因此并不会打开所有资源。  
  
 因此，为安全起见，您应检查以查看哪些资源在终止处理清理之前已实际打开。  建议的过程是：  
  
1.  将句柄初始化为 NULL。  
  
2.  在 `__try` 语句块中，分配资源。  随着资源的分配，句柄将被设置为正值。  
  
3.  在 `__finally` 语句块中，释放其对应的句柄或标志变量是非零且非 Null 的资源。  
  
## 示例  
 例如，以下代码在使用终止处理程序关闭已在 `__try` 语句块中分配的三个文件和内存块。  在清理资源之前，代码应先检查是否已分配资源。  
  
```  
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
  
## 请参阅  
 [编写终止处理程序](../cpp/writing-a-termination-handler.md)   
 [结构化异常处理](../cpp/structured-exception-handling-c-cpp.md)