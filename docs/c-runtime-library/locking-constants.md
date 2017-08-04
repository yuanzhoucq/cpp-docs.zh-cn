---
title: "_locking 常量 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _LK_RLCK
- _LK_NBLCK
- _LK_LOCK
- _LK_NBRLCK
- _LK_UNLCK
dev_langs:
- C++
helpviewer_keywords:
- LK_UNLCK constant
- LK_NBRLCK constant
- _LK_NBRLCK constant
- _LK_NBLCK constant
- _LK_LOCK constant
- LK_NBLCK constant
- _LK_UNLCK constant
- LK_RLCK constant
- _LK_RLCK constant
- LK_LOCK constant
ms.assetid: c3dc92c8-60e3-4d29-9f50-5d217627c8ad
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 6e023de61dac5679d6c46c89b57255eef0b34c76
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="locking-constants"></a>_locking 常量
## <a name="syntax"></a>语法  
  
```  
  
#include <sys/locking.h>  
  
```  
  
## <a name="remarks"></a>备注  
 `_locking` 函数调用中的 mode 参数指定要执行的锁定操作。  
  
 mode 参数必须是以下清单常量之一。  
  
 `_LK_LOCK`  
 锁定指定字节。 如果无法锁定字节，该函数会在 1 秒后再次尝试。 如果在 10 次尝试后仍无法锁定字节，该函数将返回一个错误。  
  
 `_LK_RLCK`  
 与 `_LK_LOCK` 相同。  
  
 `_LK_NBLCK`  
 锁定指定字节。 如果无法锁定字节，该函数将返回一个错误。  
  
 `_LK_NBRLCK`  
 与 `_LK_NBLCK` 相同。  
  
 `_LK_UNLCK`  
 解锁指定字节。 （这些字节必须在之前锁定。）  
  
## <a name="see-also"></a>另请参阅  
 [_locking](../c-runtime-library/reference/locking.md)   
 [全局常量](../c-runtime-library/global-constants.md)
