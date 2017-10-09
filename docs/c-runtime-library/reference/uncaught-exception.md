---
title: "__uncaught_exception | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 2
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 2b43a6b08087dcaeeda7959eaadbee9c250f4de9
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

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
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|__uncaught_exception|eh.h|  
  
## <a name="see-also"></a>另请参阅  
 [try、throw 和 catch 语句 (C++)](../../cpp/try-throw-and-catch-statements-cpp.md)
