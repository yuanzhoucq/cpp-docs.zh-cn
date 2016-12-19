---
title: "使用 VERIFY 代替 ASSERT | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "assert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ASSERT 语句"
  - "断言, 调试"
  - "断言, ASSERT 语句疑难解答"
  - "调试 [MFC], ASSERT 语句"
  - "调试断言"
  - "VERIFY 宏"
ms.assetid: 4c46397b-3fb1-49c1-a09b-41a72fae3797
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 使用 VERIFY 代替 ASSERT
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

假设在运行 MFC 应用程序的调试版本时，没有任何问题。  但是，同一应用程序的发布版本发生崩溃、返回不正确结果、并且\/或者表现出一些其他不正常行为。  
  
 当在 ASSERT 语句中放置重要代码以验证代码执行的正确性时会导致此问题。  因为 ASSERT 语句在 MFC 程序的发布版本中被注释掉了，该代码在发布版本中不会运行。  
  
 如果要使用 ASSERT 确认函数调用已成功，请考虑改用 [VERIFY](../Topic/VERIFY.md)。  VERIFY 宏在应用程序的调试版本和发布版本中都能计算自己的参数。  
  
 另一项首选技术是：将函数的返回值分配给临时变量，然后在 ASSERT 语句中测试该变量。  
  
 检查下列代码段：  
  
```  
enum {  
    sizeOfBuffer = 20  
};  
char *buf;  
ASSERT(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));  
strcpy_s( buf, sizeOfBuffer, "Hello, World" );  
free( buf );  
```  
  
 此代码在 MFC 应用程序的调试版本中运行良好。  如果 `calloc( )` 调用失败，将出现包含文件和行号的诊断消息。  然而，在 MFC 应用程序的发布版本中：  
  
-   `calloc( )` 调用永远不会发生，从而使 `buf` 保持未初始化状态，或者  
  
-   `strcpy_s( )` 将“`Hello, World`”复制到随机内存中，可能导致应用程序崩溃或系统死机，或者  
  
-   `free()` 尝试释放从未分配的内存。  
  
 要正确使用 ASSERT，应将代码示例更改为：  
  
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
  
 或者，可以改用 VERIFY：  
  
```  
enum {  
    sizeOfBuffer = 20  
};  
char *buf;  
VERIFY(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));  
strcpy_s( buf, sizeOfBuffer, "Hello, World" );  
free( buf );  
```  
  
## 请参阅  
 [修复发行版本问题](../../build/reference/fixing-release-build-problems.md)