---
title: __vmx_vmwrite |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmwrite
dev_langs:
- C++
helpviewer_keywords:
- __vmx_vmwrite intrinsic
- VMWRITE instruction
ms.assetid: 88139792-fd3f-4210-97ca-9d84f43a0252
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1f52c2c2ca60f66218b669201f293ca377d4ca5a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707013"
---
# <a name="vmxvmwrite"></a>__vmx_vmwrite
**Microsoft 专用**  
  
 将指定的值写入到当前的虚拟机控件结构 (VMCS) 中指定的字段。  
  
## <a name="syntax"></a>语法  
  
```  
unsigned char __vmx_vmwrite(   
   size_t Field,  
   size_t FieldValue  
);  
```  
  
#### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|*字段*|[in]要写入的 VMCS 字段。|  
|*FieldValue*|[in]要写入的 VMCS 字段的值。|  
  
## <a name="return-value"></a>返回值  
 0  
 操作成功。  
  
 1  
 操作失败，当前 VMCS 的 `VM-instruction error field` 中提供了扩展状态。  
  
 2  
 操作失败，无可用状态。  
  
## <a name="remarks"></a>备注  
 `__vmx_vmwrite`函数等同于`VMWRITE`计算机指令。 值`Field`参数是 Intel 文档中所述的编码的字段索引。 有关详细信息，搜索"Intel 虚拟化技术规范的 IA-32 Intel 体系结构，"文档在文档数字 C97063 002 [Intel Corporation](https://software.intel.com/en-us/articles/intel-sdm)站点，并请查阅该附录 C文档。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`__vmx_vmwrite`|X64|  
  
 **标头文件** \<intrin.h >  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmread](../intrinsics/vmx-vmread.md)