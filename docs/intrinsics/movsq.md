---
title: "__movsq | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__movsq"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__movsq 内部"
  - "rep movsq 指令"
  - "movsq 指令"
ms.assetid: be116a6e-2176-4ca4-93b1-9ccf3e7e7835
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# __movsq
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成重复移动字符串 \(`rep movsq`\) 命令。  
  
## 语法  
  
```  
void __movsq(   
   unsigned char* Dest,   
   unsigned char* Source,   
   size_t Count   
);  
```  
  
#### 参数  
 \[out\] `Dest`  
 操作的目标。  
  
 \[in\] `Source`  
 操作的源。  
  
 \[in\] `Count`  
 多次字长数要复制的。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__movsq`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 结果是第一 `Count` 多次字长指向由 `Source` 复制到 `Dest` 字符串。  
  
 此实例只能用作内部。  
  
## 示例  
  
```  
// movsq.cpp  
// processor: x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__movsq)  
  
int main()  
{  
    unsigned __int64 a1[10];  
    unsigned __int64 a2[10] = {950, 850, 750, 650, 550, 450, 350, 250,  
                               150, 50};  
    __movsq(a1, a2, 10);  
  
    for (int i = 0; i < 10; i++)  
       printf_s("%d ", a1[i]);  
    printf_s("\n");  
}  
```  
  
  **950 850 750 650 550 450 350 250 150 50**   
## 关闭 Microsoft 特定  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)