---
title: "_callnewh | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _callnewh
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _callnewh
dev_langs:
- C++
helpviewer_keywords:
- _callnewh
ms.assetid: 4dcb73e9-6384-4d12-a973-a8807d4de7a8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5754a22af15f8eca1d7352e3d172d141447a2ca4
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="callnewh"></a>_callnewh
调用当前已安装的*新处理程序*。  
  
## <a name="syntax"></a>语法  
  
```cpp  
int _callnewh(  
   size_t size  
   )  
```  
  
#### <a name="parameters"></a>参数  
 `size`  
 [新运算符](../../cpp/new-operator-cpp.md)尝试进行分配的内存量。  
  
## <a name="return-value"></a>返回值  
  
|值|描述|  
|-----------|-----------------|  
|0|失败：未安装任何新处理程序，或者无任何新处理程序处于活动状态。|  
|1|成功：新的处理程序已安装并处于活动状态。 可以重试内存分配。|  
  
## <a name="exceptions"></a>异常  
 如果找不到*新处理程序*，则此函数会引发 [bad_alloc](../../standard-library/bad-alloc-class.md)。  
  
## <a name="remarks"></a>备注  
 如果[新运算符](../../cpp/new-operator-cpp.md)未能成功分配内存，则会调用*新处理程序*。 新处理程序随后会启动一些适当的操作，如释放内存，以便成功进行后续分配。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|_callnewh|internal.h|  
  
## <a name="see-also"></a>请参阅  
 [_set_new_handler](../../c-runtime-library/reference/set-new-handler.md)   
 [_set_new_mode](../../c-runtime-library/reference/set-new-mode.md)