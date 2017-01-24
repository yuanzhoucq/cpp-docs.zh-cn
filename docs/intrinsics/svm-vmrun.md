---
title: "__svm_vmrun | Microsoft Docs"
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
  - "__svm_vmrun"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__svm_vmrun 内部函数"
  - "VMRUN 指令"
ms.assetid: ae98a781-fc17-47b2-b40f-86fcebf1867b
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __svm_vmrun
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 启动对应于指定的虚拟计算机控件块 \(VMCB\)虚拟机来宾代码的执行。  
  
## 语法  
  
```  
void __svm_vmrun(  
   size_t VmcbPhysicalAddress  
);  
```  
  
#### 参数  
  
|Parameter|说明|  
|---------------|--------|  
|\[in\] `VmcbPhysicalAddress`|VMCB 的物理地址。|  
  
## 备注  
 `__svm_vmrun` 函数在 VMCB 使用最少的信息开始执行虚拟机来宾代码。  ，如果需要更多信息处理复杂中断或切换到另一来宾，请使用 [\_\_svm\_vmsave](../intrinsics/svm-vmsave.md) 或 [\_\_svm\_vmload](../intrinsics/svm-vmload.md) 功能。  
  
 `__svm_vmrun` 功能与 `VMRUN` 指令是等效的。  此功能支持宿主的与来宾操作系统及其应用程序的虚拟机监控程序的交互。  有关更多信息，搜索文档， “AMD64 体系结构程序员的手动数量 2:系统编程，”在网站单据数字 24593，版本 3.11 或 [AMD corporation](http://go.microsoft.com/fwlink/?LinkId=23746) 更高版本，。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__svm_vmrun`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [\_\_svm\_vmsave](../intrinsics/svm-vmsave.md)   
 [\_\_svm\_vmload](../intrinsics/svm-vmload.md)