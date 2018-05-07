---
title: __vmx_vmlaunch |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmlaunch
dev_langs:
- C++
helpviewer_keywords:
- VMLAUNCH instruction
- __vmx_vmlaunch intrinsic
ms.assetid: 708f7c38-b7c1-4ee7-bfc4-0daeb9cc9360
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 926195aa8dc612d3972634f8140ce3fff753a48f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="vmxvmlaunch"></a>__vmx_vmlaunch
**Microsoft 专用**  
  
 使用当前虚拟机控件结构 (VMCS) 放置在 VMX 非根操作状态 （输入 VM） 中的调用应用程序。  
  
## <a name="syntax"></a>语法  
  
```  
unsigned char __vmx_vmlaunch(  
   void);  
```  
  
## <a name="return-value"></a>返回值  
  
|值|含义|  
|-----------|-------------|  
|0|操作成功。|  
|1|操作失败，当前 VMCS 的 `VM-instruction error field` 中提供了扩展状态。|  
|2|操作失败，无可用状态。|  
  
## <a name="remarks"></a>备注  
 应用程序可以通过使用执行 VM 输入操作[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)或[__vmx_vmresume](../intrinsics/vmx-vmresume.md)函数。 [__Vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)函数可以使用其启动状态的 vmcs `Clear`，和[__vmx_vmresume](../intrinsics/vmx-vmresume.md)函数可以使用其启动状态的 vmcs `Launched`。 因此，使用[__vmx_vmclear](../intrinsics/vmx-vmclear.md)函数可设置到 VMCS 的启动状态`Clear`，然后使用[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)函数为你的第一个 VM 输入操作和[__vmx_vmresume](../intrinsics/vmx-vmresume.md)后续 VM 输入操作的函数。  
  
 `__vmx_vmlaunch`函数等同于`VMLAUNCH`计算机指令。 此函数支持主机的虚拟机监视器与来宾操作系统及其应用程序进行交互。 有关详细信息，搜索文档中，"Intel 虚拟化技术规范为 ia-32 Intel 体系结构，"在文档编号 C97063-002， [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127)站点。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`__vmx_vmlaunch`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **标头文件** \<intrin.h >  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmresume](../intrinsics/vmx-vmresume.md)   
 [__vmx_vmclear](../intrinsics/vmx-vmclear.md)