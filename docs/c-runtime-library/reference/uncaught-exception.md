---
title: "__uncaught_exception | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- __uncaught_exception
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
apitype: DLLExport
f1_keywords:
- __uncaught_exception
dev_langs:
- C++
helpviewer_keywords:
- __uncaught_exception
ms.assetid: 4d9b75c6-c9c7-4876-b761-ea9ab1925e96
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 496947e60ab3a2b32a12b52700610aa4878ad2d0
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="uncaughtexception"></a>__uncaught_exception
指示是否已引发一个或多个异常，但是 [try-catch](../../cpp/try-throw-and-catch-statements-cpp.md) 语句的相应 `catch` 块尚未对其进行处理。  
  
## <a name="syntax"></a>语法  
  
```cpp  
bool __uncaught_exception(  
   );  
```  
  
## <a name="return-value"></a>返回值  
 自在 `try` 块中引发异常时为 `true`，直至初始化匹配的 `catch` 块；否则为 `false`。  
  
## <a name="remarks"></a>备注  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|__uncaught_exception|eh.h|  
  
## <a name="see-also"></a>请参阅  
 [try、throw 和 catch 语句 (C++)](../../cpp/try-throw-and-catch-statements-cpp.md)