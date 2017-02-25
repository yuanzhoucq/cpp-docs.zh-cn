---
title: "__movsw | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__movsw"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "movsw 指令"
  - "rep movsw 指令"
  - "__movsw 内部函数"
ms.assetid: db402ad5-7f0e-449a-b0b0-eea9928d6435
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# __movsw
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成移动字符串 \(`rep movsw`\) 命令。  
  
## 语法  
  
```  
void __movsw(   
   unsigned short* Dest,   
   unsigned short* Source,   
   size_t Count   
);  
```  
  
#### 参数  
 \[out\] `Dest`  
 操作的目标。  
  
 \[in\] `Source`  
 操作的源。  
  
 \[in\] `Count`  
 运行数要复制的。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__movsw`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 结果是第一个 `Count` 运行指向由 `Source` 复制到 `Dest` 字符串。  
  
 此实例只能用作内部。  
  
## 示例  
  
```  
// movsw.cpp  
// processor: x86, x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__movsw)  
  
int main()  
{  
    unsigned short s1[10];  
    unsigned short s2[10] = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
    __movsw(s1, s2, 10);  
  
    for (int i = 0; i < 10; i++)  
        printf_s("%d ", s1[i]);  
    printf_s("\n");  
}  
```  
  
  **0 1 2 3 4 5 6 7 8 9**   
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)