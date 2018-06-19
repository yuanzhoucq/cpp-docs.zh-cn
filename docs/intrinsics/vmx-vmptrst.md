---
title: __vmx_vmptrst |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmptrst
dev_langs:
- C++
helpviewer_keywords:
- __vmx_vmptrst intrinsic
- VMPTRST instruction
ms.assetid: 8dc66e47-03a0-41b0-8e25-c1485f42817a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ad1b6587f4386565ae7de84a7b6a170da98b6df8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33328589"
---
# <a name="vmxvmptrst"></a>__vmx_vmptrst
**Microsoft 专用**  
  
 将存储指向指定地址处的当前虚拟机控件结构 (VMCS) 的指针。  
  
## <a name="syntax"></a>语法  
  
```  
void __vmx_vmptrst(   
   unsigned __int64 *VmcsPhysicalAddress   
);  
```  
  
#### <a name="parameters"></a>参数  
 [in] *`VmcsPhysicalAddress`  
 存储当前 VMCS 指针的位置的地址。  
  
## <a name="remarks"></a>备注  
 VMCS 指针是一个 64 位物理地址。  
  
 `__vmx_vmptrst`函数等同于`VMPTRST`计算机指令。 此函数支持主机的虚拟机监视器与来宾操作系统及其应用程序进行交互。 有关详细信息，搜索文档中，"Intel 虚拟化技术规范为 ia-32 Intel 体系结构，"在文档编号 C97063-002， [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127)站点。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`__vmx_vmptrst`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **标头文件** \<intrin.h >  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmptrld](../intrinsics/vmx-vmptrld.md)