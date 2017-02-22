---
title: "__vmx_vmread | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__vmx_vmread"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VMREAD 指令"
  - "__vmx_vmread 内部函数"
ms.assetid: 08bdd7a0-6435-4ea6-b9a0-f592d870e5aa
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __vmx_vmread
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 在指定的位置读取当前虚拟计算机控制结构 \(VMCS\)和排列的指定字段它。  
  
## 语法  
  
```  
unsigned char __vmx_vmread(  
   size_t Field,  
   size_t *FieldValue  
);  
```  
  
#### 参数  
  
|Parameter|说明|  
|---------------|--------|  
|\[in\] `Field`|读取的 VMCS 字段。|  
|\[in\] `FieldValue`|将值存储位置的指针从 `Field` 参数指定的 VMCS 字段读取。|  
  
## 返回值  
  
|值|含义|  
|-------|--------|  
|0|成功的操作。|  
|1|操作 failed with 扩展的状态可用于在当前 VMCS 的 `VM-instruction error field` 。|  
|2|操作失败，但没有可用状态。|  
  
## 备注  
 `__vmx_vmread` 功能与 `VMREAD` 指令是等效的。  `Field` 参数的值是在 Intel 文档中介绍的编码域的索引。  有关更多信息，搜索文档， “IA\-32 Intel 体系结构的 Intel 虚拟化技术规范，”在网站单据数字 C97063 \-002 [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127) ，，然后参考附录 C 该文档。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__vmx_vmread`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [\_\_vmx\_vmwrite](../intrinsics/vmx-vmwrite.md)