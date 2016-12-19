---
title: "__movsd | Microsoft Docs"
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
  - "__movsd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rep movsd 指令"
  - "__movsd 内部函数"
  - "movsd 指令"
ms.assetid: eb5cccf3-aa76-47f0-b9fc-eeca38fd943f
caps.latest.revision: 14
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __movsd
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成移动字符串 \(`rep movsd`\) 命令。  
  
## 语法  
  
```  
void __movsd(   
   unsigned long* Dest,   
   unsigned long* Source,   
   size_t Count   
);  
```  
  
#### 参数  
 \[out\] `Dest`  
 操作的目标。  
  
 \[in\] `Source`  
 操作的源。  
  
 \[in\] `Count`  
 双字数要复制的。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__movsd`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 结果是第一 `Count` 双字指向由 `Source` 复制到 `Dest` 字符串。  
  
 此实例只能用作内部。  
  
## 示例  
  
```  
// movsd.cpp  
// processor: x86, x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__movsd)  
  
int main()  
{  
    unsigned long a1[10];  
    unsigned long a2[10] = {950, 850, 750, 650, 550, 450, 350,  
                            250, 150, 50};  
    __movsd(a1, a2, 10);  
  
    for (int i = 0; i < 10; i++)  
        printf_s("%d ", a1[i]);  
    printf_s("\n");  
}  
```  
  
  **950 850 750 650 550 450 350 250 150 50**   
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)