---
title: "__vmx_vmread |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __vmx_vmread
dev_langs: C++
helpviewer_keywords:
- VMREAD instruction
- __vmx_vmread intrinsic
ms.assetid: 08bdd7a0-6435-4ea6-b9a0-f592d870e5aa
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2ff3bfba5409715f2e5022e62dd74fa94360d10b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="vmxvmread"></a>__vmx_vmread
**Microsoft 专用**  
  
 从当前虚拟机控件结构 (VMCS) 中读取指定的字段，并将其放在指定的位置。  
  
## <a name="syntax"></a>语法  
  
```  
unsigned char __vmx_vmread(  
   size_t Field,  
   size_t *FieldValue  
);  
```  
  
#### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `Field`|要读取的 VMCS 字段。|  
|[in] `FieldValue`|指向要存储值的位置的读取由指定的 VMCS 字段`Field`参数。|  
  
## <a name="return-value"></a>返回值  
  
|值|含义|  
|-----------|-------------|  
|0|操作成功。|  
|1|操作失败，当前 VMCS 的 `VM-instruction error field` 中提供了扩展状态。|  
|2|操作失败，无可用状态。|  
  
## <a name="remarks"></a>备注  
 `__vmx_vmread`函数等同于`VMREAD`计算机指令。 值`Field`参数是 Intel 文档所述的编码的字段索引。 有关详细信息，搜索文档中，"Intel 虚拟化技术规范为 ia-32 Intel 体系结构，"在文档编号 C97063-002， [Intel Corporation](http://go.microsoft.com/fwlink/?LinkId=127)站点，则请查阅该文档的附录 C.  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`__vmx_vmread`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **标头文件** \<intrin.h >  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmwrite](../intrinsics/vmx-vmwrite.md)