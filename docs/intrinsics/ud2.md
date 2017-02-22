---
title: "__ud2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__ud2"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "UD2 指令"
  - "__ud2 内部函数"
ms.assetid: 0831cd5a-8b65-402e-bb57-11e1d5d7ffd2
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __ud2
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成一个未定义命令。  
  
## 语法  
  
```  
void __ud2();  
```  
  
## 备注  
 ，如果执行了未定义命令，则处理器会引发无效操作码异常。  
  
 `__ud2` 功能与 `UD2` 指令等效，并且只能在的核心架构。  有关更多信息，搜索文档， “Intel 体系结构软件开发人员的准则，数量 2:设置命令在该站点引用， [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127) ”。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__ud2`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 特定于 Microsoft 的结尾  
  
## 示例  
 下面的示例执行了未定义命令，将引发异常。  异常处理程序从零然后将返回代码添加到一个。  
  
```  
// __ud2_intrinsic.cpp  
#include <stdio.h>  
#include <intrin.h>  
#include <excpt.h>  
// compile with /EHa  
  
int main() {  
  
// Initialize the return code to 0.  
 int ret = 0;  
  
// Attempt to execute an undefined instruction.  
  printf("Before __ud2(). Return code = %d.\n", ret);  
  __try {   
  __ud2();   
  }  
  
// Catch any exceptions and set the return code to 1.  
  __except(EXCEPTION_EXECUTE_HANDLER){  
  printf("  In the exception handler.\n");  
  ret = 1;  
  }  
  
// Report the value of the return code.   
  printf("After __ud2().  Return code = %d.\n", ret);  
  return ret;  
}  
```  
  
  **在 \_\_ud2 \(\) 之前。  返回代码 \= 0。  在异常处理程序。  在 \_\_ud2 \(\) 之后。  返回代码 \= 1。**    
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)