---
title: "__writeeflags |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __writeeflags
dev_langs: C++
helpviewer_keywords: __writeeflags intrinsics
ms.assetid: a62a522c-d7fa-4f10-a620-a3b32bdf3f17
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1b87ffaacbbfee167c779f25ae83090b7b8e3397
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="writeeflags"></a>__writeeflags
指定的值写入程序状态和控制 (EFLAGS) 注册。  
  
## <a name="syntax"></a>语法  
  
```  
void __writeeflags(unsigned Value);  
void __writeeflags(unsigned __int64 Value);  
```  
  
#### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `Value`|要写入的 EFLAGS 寄存器的值。 `Value`参数为 32 位长的 32 位平台和 64 位长为 64 位平台。|  
  
## <a name="remarks"></a>备注  
 这些例程只能用作内部函数不可用。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`__writeeflags`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **标头文件** \<intrin.h >  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [__readeflags](../intrinsics/readeflags.md)