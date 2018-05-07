---
title: __stosq |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __stosq
dev_langs:
- C++
helpviewer_keywords:
- rep stosq instruction
- stosq instruction
- __stosq intrinsic
ms.assetid: 3ea28297-4369-4c2d-bf0c-91fa539ce209
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f6afd5349595f849e8b7418fa1efb628c200b4b6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="stosq"></a>__stosq
**Microsoft 专用**  
  
 生成一个存储字符串指令 (`rep stosq`)。  
  
## <a name="syntax"></a>语法  
  
```  
void __stosb(   
   unsigned __int64* Dest,   
   unsigned __int64 Data,   
   size_t Count   
);  
```  
  
#### <a name="parameters"></a>参数  
 [out] `Dest`  
 操作的目标。  
  
 [in] `Data`  
 要存储的数据。  
  
 [in] `Count`  
 四字要写入的块的长度。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`__stosq`|AMD64|  
  
 **标头文件** \<intrin.h >  
  
## <a name="remarks"></a>备注  
 结果是，四字`Data`写入到的块`Count`四字`Dest`字符串。  
  
 此例程仅可用作内部函数。  
  
## <a name="example"></a>示例  
  
```  
// stosq.c  
// processor: x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__stosq)  
  
int main()  
{  
   unsigned __int64 val = 0xFFFFFFFFFFFFI64;  
   unsigned __int64 a[10];  
   memset(a, 0, sizeof(a));  
   __stosq(a+1, val, 2);  
   printf("%I64x %I64x %I64x %I64x", a[0], a[1], a[2], a[3]);   
}  
```  
  
## <a name="output"></a>输出  
  
```  
0 ffffffffffff ffffffffffff 0  
```  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)