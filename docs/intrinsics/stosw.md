---
title: "__stosw | Microsoft Docs"
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
  - "__stosw"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "stosw 指令"
  - "__stosw 内部函数"
  - "rep stosw 指令"
ms.assetid: 7620fd1d-dba5-40e3-8e07-01aa68895133
caps.latest.revision: 15
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __stosw
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成存储字符串命令 \(`rep stosw`\)。  
  
## 语法  
  
```  
void __stosw(   
   unsigned short* Dest,   
   unsigned short Data,   
   size_t Count   
);  
```  
  
#### 参数  
 \[out\] `Dest`  
 操作的目标。  
  
 \[in\] `Data`  
 要存储的数据。  
  
 \[in\] `Count`  
 运行块的长度写入的。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__stosw`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 结果是单词 `Data` 将写入 `Count` 运行块在 `Dest` 字符串的。  
  
 此实例只能用作内部。  
  
## 示例  
  
```  
// stosw.c  
// processor: x86, x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__stosw)  
  
int main()  
{  
    unsigned short val = 128;  
    unsigned short a[100];  
    memset(a, 0, sizeof(a));  
    __stosw(a+10, val, 2);  
    printf_s("%u %u %u %u", a[9], a[10], a[11], a[12]);     
}  
```  
  
  **0 128 128 0**   
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)