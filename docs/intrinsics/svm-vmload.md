---
title: "__svm_vmload | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__svm_vmload"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__svm_vmload 内部函数"
  - "VMLOAD 指令"
ms.assetid: b46a5592-db76-4ffc-8694-2f3494e28bed
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __svm_vmload
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 从指定的虚拟计算机控件加载处理器状态的子集块 \(VMCB\)。  
  
## 语法  
  
```  
void __svm_vmload(  
   size_t VmcbPhysicalAddress  
);  
```  
  
#### 参数  
  
|Parameter|说明|  
|---------------|--------|  
|\[in\] `VmcbPhysicalAddress`|VMCB 的物理地址。|  
  
## 备注  
 `__svm_vmload` 功能与 `VMLOAD` 指令是等效的。  此功能支持宿主的与来宾操作系统及其应用程序的虚拟机监控程序的交互。  有关更多信息，搜索文档， “AMD64 体系结构程序员的手动数量 2:系统编程，”在网站单据数字 24593，版本 3.11 [AMD corporation](http://go.microsoft.com/fwlink/?LinkId=23746) 中，。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__svm_vmload`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [\_\_svm\_vmrun](../intrinsics/svm-vmrun.md)   
 [\_\_svm\_vmsave](../intrinsics/svm-vmsave.md)