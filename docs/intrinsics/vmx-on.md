---
title: "__vmx_on | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__vmx_on"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VMXON 指令"
  - "__vmx_on intrinsic"
ms.assetid: 16804991-6a75-4adf-8ec2-bc95acfa4801
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __vmx_on
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 激活虚拟机在该处理器的扩展 \(VMX\) 运算。  
  
## 语法  
  
```  
unsigned char __vmx_on(  
   unsigned __int64 *VmsSupportPhysicalAddress  
);  
```  
  
#### 参数  
 \[in\] `VmsSupportPhysicalAddress`  
 对指向虚拟设备控制结构的 64 位物理地址的指针 \(VMCS\)。  
  
## 返回值  
  
|值|含义|  
|-------|--------|  
|0|成功的操作。|  
|1|操作 failed with 扩展的状态可用于在当前 VMCS 的 `VM-instruction error field` 。|  
|2|操作失败，但没有可用状态。|  
  
## 备注  
 `__vmx_on` 函数对应于 `VMXON` 机器指令。  此功能支持宿主的与来宾操作系统及其应用程序的虚拟机监控程序的交互。  有关更多信息，搜索文档， “IA\-32 Intel 体系结构的 Intel 虚拟化技术规范，”在网站单据数字 \-002 [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127) ， C97063。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__vmx_on`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)