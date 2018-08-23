---
title: __readdr |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readdr
dev_langs:
- C++
helpviewer_keywords:
- __readdr intrinsic
ms.assetid: 061b05da-c85e-4052-b392-106f14bb84f1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd45e8919e7b1f0347511e2c3ad782975ecbe71a
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42538594"
---
# <a name="readdr"></a>__readdr
读取指定的调试寄存器的值。  
  
## <a name="syntax"></a>语法  
  
```  
unsigned         __readdr(unsigned int DebugRegister);  
unsigned __int64 __readdr(unsigned int DebugRegister);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `DebugRegister`  
 从 0 到 7 标识调试常量注册。  
  
## <a name="return-value"></a>返回值  
 指定的调试寄存器的值。  
  
## <a name="remarks"></a>备注  
 这些内部函数仅在内核模式中可用，例程只能用作内部函数。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`__readdr`|x86、x64|  
  
 **标头文件** \<intrin.h >  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [__readeflags](../intrinsics/readeflags.md)