---
title: "__svm_vmsave | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__svm_vmsave"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VMSAVE 指令"
  - "__svm_vmsave 内部函数"
ms.assetid: 617a60bd-8514-4ba1-8066-bcf4dd481030
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# __svm_vmsave
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 在指定的虚拟计算机控件存储处理器状态的子集块 \(VMCB\)。  
  
## 语法  
  
```  
void __svm_vmsave(  
   size_t VmcbPhysicalAddress  
);  
```  
  
#### 参数  
  
|Parameter|说明|  
|---------------|--------|  
|\[in\] `VmcbPhysicalAddress`|VMCB 的物理地址。|  
  
## 备注  
 `__svm_vmsave` 功能与 `VMSAVE` 指令是等效的。  此功能支持宿主的与来宾操作系统及其应用程序的虚拟机监控程序的交互。  有关更多信息，搜索文档， “AMD64 体系结构程序员的手动数量 2:系统编程，”在网站单据数字 24593，版本 3.11 或 [AMD Corporation](http://go.microsoft.com/fwlink/?LinkId=23746) 更高版本，。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__svm_vmsave`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [\_\_svm\_vmrun](../intrinsics/svm-vmrun.md)   
 [\_\_svm\_vmload](../intrinsics/svm-vmload.md)