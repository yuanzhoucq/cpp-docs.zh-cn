---
title: "__vmx_vmwrite | Microsoft Docs"
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
  - "__vmx_vmwrite"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__vmx_vmwrite intrinsic"
  - "VMWRITE 指令"
ms.assetid: 88139792-fd3f-4210-97ca-9d84f43a0252
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __vmx_vmwrite
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 写入指定的字段中指定的值与当前虚拟计算机控制结构 \(VMCS\)。  
  
## 语法  
  
```  
unsigned char __vmx_vmwrite(   
   size_t Field,  
   size_t FieldValue  
);  
```  
  
#### 参数  
  
|Parameter|说明|  
|---------------|--------|  
|\[in\] `Field`|写入的 VMCS 字段。|  
|\[in\] `FieldValue`|写入的值设置为 VMCS 字段。|  
  
## 返回值  
 0  
 成功的操作。  
  
 1  
 失败的操作以扩展的状态可用于在当前 VMCS 的 `VM-instruction error field` 。  
  
 2  
 操作失败，但没有可用状态。  
  
## 备注  
 `__vmx_vmwrite` 功能与 `VMWRITE` 指令是等效的。  `Field` 参数的值是在 Intel 文档中介绍的编码域的索引。  有关更多信息，搜索文档， “IA\-32 Intel 体系结构的 Intel 虚拟化技术规范，”在网站单据数字 C97063 \-002 [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127) ，，然后参考附录 C 该文档。  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__vmx_vmwrite`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [\_\_vmx\_vmread](../intrinsics/vmx-vmread.md)