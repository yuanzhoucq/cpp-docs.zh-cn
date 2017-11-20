---
title: "__readdr |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __readdr
dev_langs: C++
helpviewer_keywords: __readdr intrinsic
ms.assetid: 061b05da-c85e-4052-b392-106f14bb84f1
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f167001e8202b950e1e994e7a4ed53b40a50ded4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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
 这些内部函数仅在内核模式下适用而例程只能用作内部函数。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`__readdr`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **标头文件** \<intrin.h >  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [__readeflags](../intrinsics/readeflags.md)