---
title: "_abnormal_termination |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _abnormal_termination
apilocation:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- _abnormal_termination
dev_langs:
- C++
helpviewer_keywords:
- _abnormal_termination
ms.assetid: 952970a4-9586-4c3d-807a-db729448c91c
caps.latest.revision: 2
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: d826dd3c0293393a960657f45ac4b68370d7030c
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="abnormaltermination"></a>_abnormal_termination
指示是否在系统执行终止处理程序的内部列表时进入 [try-finally 语句](../cpp/try-finally-statement.md)的 `__finally` 块。  
  
## <a name="syntax"></a>语法  
  
```cpp  
int   _abnormal_termination(  
   );  
```  
  
## <a name="return-value"></a>返回值  
 如果系统*展开*堆栈，则为 `true`；否则为 `false`。  
  
## <a name="remarks"></a>备注  
 这是用于管理展开异常的内部函数，并且不应从用户代码调用。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|_abnormal_termination|excpt.h|  
  
## <a name="see-also"></a>另请参阅  
 [try-finally 语句](../cpp/try-finally-statement.md)
