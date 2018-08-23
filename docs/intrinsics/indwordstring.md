---
title: __indwordstring |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __indwordstring
- __indwordstring_cpp
dev_langs:
- C++
helpviewer_keywords:
- __indwordstring intrinsic
- rep insd instruction
ms.assetid: 96a1cf33-f691-4916-99e4-fa849b61e3a9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 00c0f8e67a535d126eab3a19bf17b0bf8bfd7440
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42540154"
---
# <a name="indwordstring"></a>__indwordstring
**Microsoft 专用**  
  
 从指定的端口使用读取数据`rep insd`指令。  
  
## <a name="syntax"></a>语法  
  
```  
void __indwordstring(  
   unsigned short Port,  
   unsigned long* Buffer,  
   unsigned long Count  
);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `Port`  
 要读取的端口。  
  
 [out] `Buffer`  
 读取从端口将数据写入此处。  
  
 [in] `Count`  
 要读取的数据的字节数。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`__indwordstring`|x86、x64|  
  
 **标头文件** \<intrin.h >  
  
## <a name="remarks"></a>备注  
 此例程仅可用作内部函数。  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)