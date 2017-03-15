---
title: "__svm_skinit | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__svm_skinit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SKINIT 指令"
  - "__svm_skinit 内部函数"
ms.assetid: 787ec781-4cf2-40a2-aa20-5192334b131a
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __svm_skinit
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 启动可验证为安全软件加载，如虚拟机监控程序。  
  
## 语法  
  
```  
void __svm_skinit(  
   int SLB  
);  
```  
  
#### 参数  
  
|Parameter|说明|  
|---------------|--------|  
|`SLB`|一个 64K 字节的 32 位物理地址保护程序集 \(SLB\)块。|  
  
## 备注  
 `__svm_skinit` 功能与 `SKINIT` 指令是等效的。  此函数是使用该处理器，并验证和加载受信任的平台模块 \(TPM\)信任调用安全核心的软件安全系统的一部分 \(SK\)。  虚拟机监控程序是安全核心的示例。  安全系统验证在中加载的程序元素初始化过程，以及中断、设备访问，或另一个程序防止篡改的元素，如果计算机是多处理器。  
  
 `SLB` 参数指定 64K 的物理地址调用 *安全的* 内存块 *程序集块 \(SLB\)* 。  SLB 包含调用建立计算机上运行环境的安全加载程序的程序及随后加载安全核心。  
  
 此功能支持宿主的与来宾操作系统及其应用程序的虚拟机监控程序的交互。  有关更多信息，搜索文档， “AMD64 体系结构程序员的手动数量 2:系统编程，”在网站单据数字 24593，版本 3.11 [AMD corporation](http://go.microsoft.com/fwlink/?LinkId=23746) 中，。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__svm_skinit`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)