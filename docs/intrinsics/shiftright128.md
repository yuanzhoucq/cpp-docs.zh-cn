---
title: __shiftright128 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __shiftright128
dev_langs:
- C++
helpviewer_keywords:
- __shiftright128 intrinsic
ms.assetid: 5419a6c4-0de1-43fb-b314-4faa5b2d051f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 15c166f51e8d512dd0c5ef8d98bf1e6cf991664f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714202"
---
# <a name="shiftright128"></a>__shiftright128
**Microsoft 专用**  
  
 将 128 位数量（表示为两个 64 位数量 `LowPart` 和 `HighPart`）按 `Shift` 指定的位数右移并返回低 64 位结果。  
  
## <a name="syntax"></a>语法  
  
```  
unsigned __int64 __shiftright128(   
   unsigned __int64 LowPart,   
   unsigned __int64 HighPart,   
   unsigned char Shift   
);  
```  
  
#### <a name="parameters"></a>参数  
*LowPart*<br/>
[in]要位移的 128 位数量的低 64 位。  
  
*HighPart*<br/>
[in]要位移的 128 位数量高 64 位。  
  
*Shift*<br/>
[in]移动的位数数。  
  
## <a name="return-value"></a>返回值  
 结果的低 64 位。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`__shiftright128`|X64|  
  
 **标头文件** \<intrin.h >  
  
## <a name="remarks"></a>备注  
 `Shift` 值始终是模 64，如果调用 `__shiftright128(0, 1, 64)`，该函数将向右位移高部分 `0` 位并返回低部分的 `0` 而不是另外预期的 `1`。  
  
## <a name="example"></a>示例  
 有关示例，请参阅[__shiftleft128](../intrinsics/shiftleft128.md)。  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [__shiftleft128](../intrinsics/shiftleft128.md)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)