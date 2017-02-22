---
title: "__vmx_vmclear | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__vmx_vmclear"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VMCLEAR 指令"
  - "__vmx_vmclear 内部函数"
ms.assetid: e3eb98e4-50fc-4c93-9bac-340fd1f0a466
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __vmx_vmclear
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 初始化指定的虚拟计算机控制结构 \(VMCS\)并将其生成状态到 `Clear`。  
  
## 语法  
  
```  
unsigned char __vmx_vmclear(  
   unsigned __int64 *VmcsPhysicalAddress  
);  
```  
  
#### 参数  
  
|Parameter|说明|  
|---------------|--------|  
|\[in\] `VmcsPhysicalAddress`|对包含 VMCS 物理地址清除的 64 位内存位置的指针。|  
  
## 返回值  
  
|值|含义|  
|-------|--------|  
|0|成功的操作。|  
|1|失败的操作以扩展的状态可用于在当前 VMCS 的 `VM-instruction error field` 。|  
|2|操作失败，但没有可用状态。|  
  
## 备注  
 使用 [\_\_vmx\_vmlaunch](../intrinsics/vmx-vmlaunch.md) 或 [\_\_vmx\_vmresume](../intrinsics/vmx-vmresume.md) 功能，应用程序可以执行 VM 输入操作。  [\_\_vmx\_vmlaunch](../intrinsics/vmx-vmlaunch.md) 函数只能用于生成状态是 `Clear`的 VMCS，并且， [\_\_vmx\_vmresume](../intrinsics/vmx-vmresume.md) 函数只能用于生成状态是 `Launched`的 VMCS。  结果，请使用 [\_\_vmx\_vmclear](../intrinsics/vmx-vmclear.md) 功能集 VMCS 的生成状态到 `Clear`。  对于第一使用 [\_\_vmx\_vmlaunch](../intrinsics/vmx-vmlaunch.md) 功能 VM 输入操作，后面的 [\_\_vmx\_vmresume](../intrinsics/vmx-vmresume.md) 功能 VM 输入操作。  
  
 `__vmx_vmclear` 功能与 `VMCLEAR` 指令是等效的。  此功能支持宿主的与来宾操作系统及其应用程序的虚拟机监控程序的交互。  有关更多信息，搜索文档， “IA\-32 Intel 体系结构的 Intel 虚拟化技术规范，”在网站单据数字 \-002 [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127) ， C97063。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__vmx_vmclear`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [\_\_vmx\_vmlaunch](../intrinsics/vmx-vmlaunch.md)   
 [\_\_vmx\_vmresume](../intrinsics/vmx-vmresume.md)