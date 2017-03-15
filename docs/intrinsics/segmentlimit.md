---
title: "__segmentlimit | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__segmentlimit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__segmentlimit 内部函数"
  - "lsl 指令"
ms.assetid: d0bc3630-90cb-4185-8667-686fd41e23d4
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# __segmentlimit
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成 `lsl` \(加载段限制\) 命令。  
  
## 语法  
  
```  
unsigned long __segmentlimit(   
   unsigned long a   
);  
```  
  
#### 参数  
 \[in\] `a`  
 指定段选择器中的常数。  
  
## 返回值  
 `a,`指定时间段选择器的段限制，在该有效并显示在当前权限级别条件下。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__segmentlimit`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 如果段限制不能检索，此命令失败。  在失败时，此命令清除 ZF 标志，并返回值是不确定的。  
  
 此实例只能用作内部。  
  
## 示例  
  
```  
#include <stdio.h>  
  
#ifdef _M_IX86  
typedef unsigned int READETYPE;  
#else  
typedef unsigned __int64 READETYPE;  
#endif  
  
#define EFLAGS_ZF      0x00000040  
#define KGDT_R3_DATA    0x0020  
#define RPL_MASK        0x3  
  
extern "C"  
{  
unsigned long __segmentlimit (unsigned long);  
READETYPE __readeflags();  
}  
  
#pragma intrinsic(__readeflags)  
#pragma intrinsic(__segmentlimit)  
  
int main(void)  
{  
   const unsigned long initsl = 0xbaadbabe;  
   READETYPE eflags = 0;  
   unsigned long sl = initsl;  
  
   printf("Before: segment limit =0x%x eflags =0x%x\n", sl, eflags);  
   sl = __segmentlimit(KGDT_R3_DATA + RPL_MASK);  
  
   eflags = __readeflags();  
  
   printf("After: segment limit =0x%x eflags =0x%x eflags.zf = %s\n", sl, eflags, (eflags & EFLAGS_ZF) ? "set" : "clear");  
  
   // If ZF is set, the call to lsl succeeded; if ZF is clear, the call failed.  
   printf("%s\n", eflags & EFLAGS_ZF ? "Success!": "Fail!");  
  
   // You can verify the value of sl to make sure that the instruction wrote to it  
   printf("sl was %s\n", (sl == initsl) ? "unchanged" : "changed");  
  
   return 0;  
}  
```  
  
  **以前:段限制 \=0xbaadbabe eflags \=0x0**  
**后面:段限制 \=0xffffffff eflags \=0x256 eflags.zf \= 设置**  
**成功！  已更改 sl**    
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)