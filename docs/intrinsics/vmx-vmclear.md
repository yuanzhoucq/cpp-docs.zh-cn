---
title: __vmx_vmclear |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmclear
dev_langs:
- C++
helpviewer_keywords:
- VMCLEAR instruction
- __vmx_vmclear intrinsic
ms.assetid: e3eb98e4-50fc-4c93-9bac-340fd1f0a466
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8da1e3d2c5b1a2018df0e46f085fede9b923fff8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332405"
---
# <a name="vmxvmclear"></a>__vmx_vmclear
**Microsoft 专用**  
  
 初始化指定的虚拟机控件结构 (VMCS) 并将其启动状态设置为`Clear`。  
  
## <a name="syntax"></a>语法  
  
```  
unsigned char __vmx_vmclear(  
   unsigned __int64 *VmcsPhysicalAddress  
);  
```  
  
#### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in] `VmcsPhysicalAddress`|指向包含 VMCS 清除的物理地址的 64 位内存位置的指针。|  
  
## <a name="return-value"></a>返回值  
  
|值|含义|  
|-----------|-------------|  
|0|操作成功。|  
|1|操作失败，当前 VMCS 的 `VM-instruction error field` 中提供了扩展状态。|  
|2|操作失败，无可用状态。|  
  
## <a name="remarks"></a>备注  
 应用程序可以通过使用执行 VM 输入操作[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)或[__vmx_vmresume](../intrinsics/vmx-vmresume.md)函数。 [__Vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)函数可以使用其启动状态的 vmcs `Clear`，和[__vmx_vmresume](../intrinsics/vmx-vmresume.md)函数可以使用其启动状态的 vmcs `Launched`。 因此，使用[__vmx_vmclear](../intrinsics/vmx-vmclear.md)函数可设置到 VMCS 的启动状态`Clear`。 使用[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)为第一个 VM 输入操作的函数和[__vmx_vmresume](../intrinsics/vmx-vmresume.md)后续 VM 输入操作的函数。  
  
 `__vmx_vmclear`函数等同于`VMCLEAR`计算机指令。 此函数支持主机的虚拟机监视器与来宾操作系统及其应用程序进行交互。 有关详细信息，搜索文档中，"Intel 虚拟化技术规范为 ia-32 Intel 体系结构，"在文档编号 C97063-002， [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127)站点。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`__vmx_vmclear`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **标头文件** \<intrin.h >  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)   
 [__vmx_vmresume](../intrinsics/vmx-vmresume.md)