---
title: __vmx_on |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_on
dev_langs:
- C++
helpviewer_keywords:
- VMXON instruction
- __vmx_on intrinsic
ms.assetid: 16804991-6a75-4adf-8ec2-bc95acfa4801
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e01be3d3f7db075116782b64e8b92ba12fb02f1d
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42539750"
---
# <a name="vmxon"></a>__vmx_on
**Microsoft 专用**  
  
 激活处理器中的虚拟机扩展 (VMX) 操作。  
  
## <a name="syntax"></a>语法  
  
```  
unsigned char __vmx_on(  
   unsigned __int64 *VmsSupportPhysicalAddress  
);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `VmsSupportPhysicalAddress`  
 指向虚拟机控件结构 (VMCS) 的 64 位物理地址的指针。  
  
## <a name="return-value"></a>返回值  
  
|“值”|含义|  
|-----------|-------------|  
|0|操作成功。|  
|1|操作失败，当前 VMCS 的 `VM-instruction error field` 中提供了扩展状态。|  
|2|操作失败，无可用状态。|  
  
## <a name="remarks"></a>备注  
 `__vmx_on`函数对应于`VMXON`计算机指令。 此函数支持主机的虚拟机监视器与来宾操作系统及其应用程序进行交互。 有关详细信息，搜索"Intel 虚拟化技术规范的 IA-32 Intel 体系结构，"文档在文档数字 C97063 002 [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127)站点。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`__vmx_on`|X64|  
  
 **标头文件** \<intrin.h >  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)