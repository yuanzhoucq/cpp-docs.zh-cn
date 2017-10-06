---
title: _except_handler3 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _except_handler3
apilocation:
- msvcrt.dll
- msvcr90.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- _except_handler3
- except_handler3
dev_langs:
- C++
helpviewer_keywords:
- _except_handler3 function
- except_handler3 function
ms.assetid: b0c64898-0ae5-48b7-9724-80135a0813e2
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: ce3717ea39cec55ab982de3c9d8fddd0b50632ee
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="excepthandler3"></a>_except_handler3
内部 CRT 函数。 由框架用于查找相应的异常处理程序，以处理当前异常。  
  
## <a name="syntax"></a>语法  
  
```  
int _except_handler3(  
   PEXCEPTION_RECORD exception_record,  
   PEXCEPTION_REGISTRATION registration,  
   PCONTEXT context,  
   PEXCEPTION_REGISTRATION dispatcher  
);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `exception_record`  
 有关特定异常的信息。  
  
 [in] `registration`  
 指示应该使用哪一个范围表查找异常处理程序的记录。  
  
 [in] `context`  
 保留。  
  
 [in] `dispatcher`  
 保留。  
  
## <a name="return-value"></a>返回值  
 如果应该消除某个异常，则返回 `DISPOSITION_DISMISS`。 如果应该将异常向上传递一个等级给封装的异常处理程序，则返回 `DISPOSITION_CONTINUE_SEARCH`。  
  
## <a name="remarks"></a>备注  
 如果此方法找到了相应的异常处理程序，则它会将异常传递给该处理程序。 在这种情况下，此方法不会返回到调用它的代码且与返回值无关。  
  
## <a name="see-also"></a>另请参阅  
 [按字母顺序的函数参考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)
