---
title: __writecr4 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _writecr4
dev_langs:
- C++
helpviewer_keywords:
- _writecr4 intrinsic
ms.assetid: ab7651d7-b86b-4be7-a0a0-7263099c70fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 097be395b26935b1c889a5ed542da3f544501ceb
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42545768"
---
# <a name="writecr4"></a>__writecr4
**Microsoft 专用**  
  
 将值写入`Data`CR4 注册。  
  
## <a name="syntax"></a>语法  
  
```  
void writecr4(   
   unsigned __int64 Data   
);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `Data`  
 要写入到 CR4 寄存器的值。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`__writecr4`|x86、x64|  
  
 **标头文件** \<intrin.h >  
  
## <a name="remarks"></a>备注  
 此内部函数只在内核模式下可用，例程只能用作内部函数。  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)