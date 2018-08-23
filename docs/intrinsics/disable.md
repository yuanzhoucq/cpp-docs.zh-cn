---
title: _disable |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _disable_cpp
- _disable
dev_langs:
- C++
helpviewer_keywords:
- _disable intrinsic
- rsm instruction
- disable intrinsic
ms.assetid: 52da3df9-815c-4524-9839-6d1742cff5c6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2748d0412c9ee0f7e7684d35a38f3c2b5d133754
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42540185"
---
# <a name="disable"></a>_disable
**Microsoft 专用**  
  
 禁用中断。  
  
## <a name="syntax"></a>语法  
  
```  
void _disable(void);  
```  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`_disable`|x86、 ARM、 x64|  
  
 **标头文件** \<intrin.h >  
  
## <a name="remarks"></a>备注  
 `_disable` 指示处理器去清除中断标记。 在 x86 系统上，此函数会生成“清除中断标记”(`cli`) 指令。  
  
 此函数只有在内核模式下才可用。 如果在用户模式下使用，运行时会出现特权指令异常。  
  
 在 ARM 平台上，此例程只能用作内部函数。  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)