---
title: "__vmx_vmlaunch | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__vmx_vmlaunch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VMLAUNCH 指令"
  - "__vmx_vmlaunch intrinsic"
ms.assetid: 708f7c38-b7c1-4ee7-bfc4-0daeb9cc9360
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __vmx_vmlaunch
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 在 VMX 非根的操作状态将调用应用程序 \(VM 键入\) 使用当前虚拟设备控制结构， \(VMCS\)。  
  
## 语法  
  
```  
unsigned char __vmx_vmlaunch(  
   void);  
```  
  
## 返回值  
  
|值|含义|  
|-------|--------|  
|0|成功的操作。|  
|1|操作 failed with 扩展的状态可用于在当前 VMCS 的 `VM-instruction error field` 。|  
|2|操作失败，但没有可用状态。|  
  
## 备注  
 使用 [\_\_vmx\_vmlaunch](../intrinsics/vmx-vmlaunch.md) 或 [\_\_vmx\_vmresume](../intrinsics/vmx-vmresume.md) 功能，应用程序可以执行 VM 输入操作。  [\_\_vmx\_vmlaunch](../intrinsics/vmx-vmlaunch.md) 函数只能用于生成状态是 `Clear`的 VMCS，并且， [\_\_vmx\_vmresume](../intrinsics/vmx-vmresume.md) 函数只能用于生成状态是 `Launched`的 VMCS。  结果，请使用 [\_\_vmx\_vmclear](../intrinsics/vmx-vmclear.md) 功能集 VMCS 的生成状态到 `Clear`，对于第一然后使用 [\_\_vmx\_vmlaunch](../intrinsics/vmx-vmlaunch.md) 功能 VM 输入操作，后面的 [\_\_vmx\_vmresume](../intrinsics/vmx-vmresume.md) 功能 VM 输入操作。  
  
 `__vmx_vmlaunch` 功能与 `VMLAUNCH` 指令是等效的。  此功能支持宿主的与来宾操作系统及其应用程序的虚拟机监控程序的交互。  有关更多信息，搜索文档， “IA\-32 Intel 体系结构的 Intel 虚拟化技术规范，”在网站单据数字 \-002 [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127) ， C97063。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__vmx_vmlaunch`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [\_\_vmx\_vmresume](../intrinsics/vmx-vmresume.md)   
 [\_\_vmx\_vmclear](../intrinsics/vmx-vmclear.md)