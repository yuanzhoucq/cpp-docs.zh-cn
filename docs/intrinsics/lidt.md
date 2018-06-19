---
title: __lidt |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __lidt
- __lidt_cpp
dev_langs:
- C++
helpviewer_keywords:
- LIDT instruction
- __lidt intrinsic
ms.assetid: 8298d25d-a19e-4900-828d-6b3b09841882
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8dd972d2a7e8d75f7149b2dc2766ffca86b0b2e5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33326506"
---
# <a name="lidt"></a>__lidt
**Microsoft 专用**  
  
 加载指定的内存位置中的值的中断描述符表寄存器 (IDTR)。  
  
## <a name="syntax"></a>语法  
  
```  
void __lidt(  
     void *Source);  
```  
  
#### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in] `Source`|指向要复制到 IDTR 的值的指针。|  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`__lidt`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **标头文件** \<intrin.h >  
  
## <a name="remarks"></a>备注  
 `__lidt`函数等同于`LIDT`计算机指令，并仅在内核模式中可用。 有关详细信息，搜索文档中，"Intel 体系结构软件开发人员手册，卷 2： 指令集引用，"在[Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127)站点。  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [__sidt](../intrinsics/sidt.md)