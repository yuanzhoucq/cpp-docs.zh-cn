---
title: __inwordstring |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __inwordstring
- __inwordstring_cpp
dev_langs:
- C++
helpviewer_keywords:
- __inwordstring intrinsic
- rep insw instruction
ms.assetid: 6de37939-017a-4740-9e3d-7de78a30daba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb3f563d94d2e7685c1a83e497b1db082f131842
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42545766"
---
# <a name="inwordstring"></a>__inwordstring
**Microsoft 专用**  
  
 从指定的端口使用读取数据`rep insw`指令。  
  
## <a name="syntax"></a>语法  
  
```  
void __inwordstring(  
   unsigned short Port,  
   unsigned short* Buffer,  
   unsigned long Count  
);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `Port`  
 要读取的端口。  
  
 [out] `Buffer`  
 读取从端口将数据写入此处。  
  
 [in] `Count`  
 要读取的数据的单词数。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`__inwordstring`|x86、x64|  
  
 **标头文件** \<intrin.h >  
  
## <a name="remarks"></a>备注  
 此例程仅可用作内部函数。  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)