---
title: "__vmx_vmptrst | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__vmx_vmptrst"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__vmx_vmptrst 指令"
  - "VMPTRST 指令"
ms.assetid: 8dc66e47-03a0-41b0-8e25-c1485f42817a
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __vmx_vmptrst
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 存储指向当前虚拟设备控制 \(VMCS\)结构在指定的地址。  
  
## 语法  
  
```  
void __vmx_vmptrst(   
   unsigned __int64 *VmcsPhysicalAddress   
);  
```  
  
#### 参数  
 \[in\] \*`VmcsPhysicalAddress`  
 存储当前 VMCS 指针的地址。  
  
## 备注  
 VMCS 指针是一个 64位物理地址。  
  
 `__vmx_vmptrst` 功能与 `VMPTRST` 指令是等效的。  此功能支持宿主的与来宾操作系统及其应用程序的虚拟机监控程序的交互。  有关更多信息，搜索文档， “IA\-32 Intel 体系结构的 Intel 虚拟化技术规范，”在网站单据数字 \-002 [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127) ， C97063。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__vmx_vmptrst`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [\_\_vmx\_vmptrld](../intrinsics/vmx-vmptrld.md)