---
title: "_findclose | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _findclose
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _findclose
- findclose
dev_langs:
- C++
helpviewer_keywords:
- _findclose function
- findclose function
ms.assetid: 9216c573-0878-444c-b5d7-cdaf16fb9163
caps.latest.revision: 11
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: fcd76f8daec9c90374989a82f4b4b2f85b4cb5c7
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="findclose"></a>_findclose
关闭指定的搜索句柄并释放关联资源。  
  
## <a name="syntax"></a>语法  
  
```  
int _findclose(   
   intptr_t handle   
);  
```  
  
#### <a name="parameters"></a>参数  
 `handle`  
 搜索由以前调用 `_findfirst` 返回的句柄。  
  
## <a name="return-value"></a>返回值  
 如果成功，则 `_findclose` 返回 0。 否则，它将返回-1 并将设置`errno`到`ENOENT`，无法找到，该值指示没有更多匹配的文件。  
  
## <a name="requirements"></a>要求  
  
|函数|必需的标头|  
|--------------|---------------------|  
|`_findclose`|\<io.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另请参阅  
 [系统调用](../../c-runtime-library/system-calls.md)   
 [文件名搜索函数](../../c-runtime-library/filename-search-functions.md)
