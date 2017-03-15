---
title: "__movsb | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__movsb"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "movsb 指令"
  - "rep movsb 指令"
  - "__movsb 内部函数"
ms.assetid: ba5469f6-f797-4cd2-bee8-74c7666c26d4
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# __movsb
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成移动字符串 \(`rep movsb`\) 命令。  
  
## 语法  
  
```  
void __movsb(   
   unsigned char* Destination,   
   unsigned const char* Source,   
   size_t Count   
);  
```  
  
#### 参数  
 \[out\] `Destination`  
 要复制的目标的指针。  
  
 \[in\] `Source`  
 要复制的源的指针。  
  
 \[in\] `Count`  
 要复制的字节数。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__movsb`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 结果是第一个 `Count` 字节指向由 `Source` 复制到 `Destination` 字符串。  
  
 此实例只能用作内部。  
  
## 示例  
  
```  
// movsb.cpp  
// processor: x86, x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__movsb)  
  
int main()  
{  
    unsigned char s1[100];  
    unsigned char s2[100] = "A big black dog.";  
    __movsb(s1, s2, 100);  
  
    printf_s("%s %s", s1, s2);  
}  
```  
  
  **用按下。  用按下。**    
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)