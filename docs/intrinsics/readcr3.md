---
title: __readcr3 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readcr3
dev_langs:
- C++
helpviewer_keywords:
- __readcr3 intrinsic
ms.assetid: e24392c3-cad7-4788-8f31-94bf2e9e0053
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 486a21506ea4b8c388dcf495f348987c3464ddc6
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42539196"
---
# <a name="readcr3"></a>__readcr3
**Microsoft 专用**  
  
 读取 CR3 寄存器并返回其值。  
  
## <a name="syntax"></a>语法  
  
```  
unsigned __int64 __readcr3(void);  
```  
  
## <a name="return-value"></a>返回值  
 CR3 寄存器中的值。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`__readcr3`|x86、x64|  
  
 **标头文件** \<intrin.h >  
  
## <a name="remarks"></a>备注  
 此内部函数只在内核模式下可用，例程只能用作内部函数。  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)