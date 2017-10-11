---
title: "_CxxThrowException | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CxxThrowException
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
- CxxThrowException
- _CxxThrowException
dev_langs:
- C++
helpviewer_keywords:
- _CxxThrowException function
- CxxThrowException function
ms.assetid: 0b90bef5-b7d2-46e0-88e2-59e531e01a4d
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 5cfe894dc20e77bf34067c16fddd74432c522bda
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="cxxthrowexception"></a>_CxxThrowException
生成异常记录并调用运行时环境以开始处理异常。  
  
## <a name="syntax"></a>语法  
  
```  
extern "C" void __stdcall _CxxThrowException(  
   void* pExceptionObject  
   _ThrowInfo* pThrowInfo  
);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `pExceptionObject`  
 生成异常的对象。  
  
 [in] `pThrowInfo`  
 处理异常所需的信息。  
  
## <a name="remarks"></a>备注  
 此方法包含在编译器用来处理异常的仅编译器文件中。 不要直接从代码调用方法。  
  
## <a name="requirements"></a>要求  
 **源：**Throw.cpp  
  
## <a name="see-also"></a>另请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)
