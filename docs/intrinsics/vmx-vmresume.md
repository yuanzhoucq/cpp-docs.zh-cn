---
title: "__vmx_vmresume | Microsoft Docs"
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
  - "__vmx_vmresume"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__vmx_vmresume 内部函数"
  - "VMRESUME 指令"
ms.assetid: 233fe1b6-c727-493a-a484-1b2363732281
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __vmx_vmresume
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 通过使用当前虚拟机控件结构 \(VMCS\) 恢复 VMX 非根操作。  
  
## 语法  
  
```  
unsigned char __vmx_vmresume(  
   void);  
```  
  
## 返回值  
  
|值|含义|  
|-------|--------|  
|0|操作成功。|  
|1|操作失败，当前 VMCS 的 `VM-instruction error field` 中提供了扩展状态。|  
|2|操作失败，无可用状态。|  
  
## 备注  
 应用程序可以通过使用 [\_\_vmx\_vmlaunch](../intrinsics/vmx-vmlaunch.md) 或 `__vmx_vmresume` 函数执行 VM 输入操作。`__vmx_vmlaunch` 函数只可用于启动状态为 `Clear` 的 VMCS，而 `__vmx_vmresume` 函数只可用于启动状态为 `Launched` 的 VMCS。 因此，使用 [\_\_vmx\_vmclear](../intrinsics/vmx-vmclear.md) 函数将 VMCS 的启动状态设置为 `Clear`，然后对第一个 VM 输入操作使用 `__vmx_vmlaunch` 函数，对后续 VM 输入操作使用 `__vmx_vmresume` 函数。  
  
 `__vmx_vmresume` 函数等同于 `VMRESUME` 计算机指令。 此函数支持主机的虚拟机监视器与来宾操作系统及其应用程序进行交互。 有关详细信息，请在 [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127) 站点搜索 PDF 文档“适用于 IA\-32 Intel 架构的 Intel 虚拟化技术规范”，文档编号 C97063\-002。  
  
## 要求  
  
|内部函数|体系结构|  
|----------|----------|  
|`__vmx_vmresume`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [\_\_vmx\_vmlaunch](../intrinsics/vmx-vmlaunch.md)   
 [\_\_vmx\_vmclear](../intrinsics/vmx-vmclear.md)