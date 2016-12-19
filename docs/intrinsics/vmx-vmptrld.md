---
title: "__vmx_vmptrld | Microsoft Docs"
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
  - "__vmx_vmptrld"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__vmx_vmptrld 内部函数"
  - "VMPTRLD 指令"
ms.assetid: 95c9ec5b-1a81-41ba-983e-327bd6a65fcb
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __vmx_vmptrld
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 加载指向当前虚拟设备控制 \(VMCS\)结构从指定的地址。  
  
## 语法  
  
```  
int __vmx_vmptrld(   
   unsigned __int64 *VmcsPhysicalAddress   
);  
```  
  
#### 参数  
 \[in\] \*`VmcsPhysicalAddress`  
 存储 VMCS 指针的地址。  
  
## 返回值  
 0  
 成功的操作。  
  
 1  
 操作 failed with 扩展的状态可用于在当前 VMCS 的 `VM-instruction error field` 。  
  
 2  
 操作失败，但没有可用状态。  
  
## 备注  
 VMCS 指针是一个 64位物理地址。  
  
 `__vmx_vmptrld` 功能与 `VMPTRLD` 指令是等效的。  此功能支持宿主的与来宾操作系统及其应用程序的虚拟机监控程序的交互。  有关更多信息，搜索文档， “IA\-32 Intel 体系结构的 Intel 虚拟化技术规范，”在网站单据数字 \-002 [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127) ， C97063。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__vmx_vmptrld`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [\_\_vmx\_vmptrst](../intrinsics/vmx-vmptrst.md)