---
title: __CxxFrameHandler | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: __CxxFrameHandler
apilocation:
- msvcr110.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords: __CxxFrameHandler
dev_langs: C++
helpviewer_keywords: __CxxFrameHandler
ms.assetid: b79ac97f-425a-42ae-9b91-8beaef935333
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 75f900560f226557bc160bdf74df4467b0c7aa32
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="cxxframehandler"></a>__CxxFrameHandler
内部 CRT 函数。 由 CRT 用于处理结构化异常帧。  
  
## <a name="syntax"></a>语法  
  
```cpp  
EXCEPTION_DISPOSITION __CxxFrameHandler(  
      EHExceptionRecord  *pExcept,  
      EHRegistrationNode *pRN,  
      void               *pContext,   
      DispatcherContext  *pDC  
   )  
```  
  
#### <a name="parameters"></a>参数  
 `pExcept`  
 传递给可能的 `catch` 语句的异常记录。  
  
 `pRN`  
 有关用于处理异常的堆栈帧的动态信息。 有关详细信息，请参阅 ehdata.h。  
  
 `pContext`  
 上下文。 （不可用于 Intel 处理器上。）  
  
 `pDC`  
 有关函数入口和堆栈帧的其他信息。  
  
## <a name="return-value"></a>返回值  
 由 [try-except 语句](../cpp/try-except-statement.md)使用的 filter expression 值之一。  
  
## <a name="remarks"></a>备注  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|__CxxFrameHandler|excpt.h，ehdata.h|