---
title: __writedr |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __writedr
dev_langs:
- C++
helpviewer_keywords:
- __writedr intrinsic
ms.assetid: ac55c1ee-df2f-41d4-a429-6f369d2a934d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 598b95df8fd2f4dd2826fcfa1f59a7e2daa8d523
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42539200"
---
# <a name="writedr"></a>__writedr
将指定的值写入到指定的调试注册。  
  
## <a name="syntax"></a>语法  
  
```  
void __writedr(unsigned DebugRegister, unsigned DebugValue);  
void __writedr(unsigned DebugRegister, unsigned __int64 DebugValue);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `DebugRegister`  
 一个介于 0 到 7 标识调试注册。  
  
 [in] `DebugValue`  
 一个值，以写入调试注册。  
  
## <a name="remarks"></a>备注  
 这些内部函数仅在内核模式中可用，例程只能用作内部函数。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`__writedr`|x86、x64|  
  
 **标头文件** \<intrin.h >  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [__readdr](../intrinsics/readdr.md)