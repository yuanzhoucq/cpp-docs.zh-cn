---
title: "__p__commode | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- __p__commode
apilocation:
- msvcr110.dll
- msvcrt.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __p__commode
dev_langs:
- C++
helpviewer_keywords:
- __p__commode
ms.assetid: 4380acb8-e3e4-409c-a60f-6205ac5189ce
caps.latest.revision: 2
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: cdb058b0173e15d17f47a90d6101aca65954c814
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="pcommode"></a>__p__commode
指向 `_commode` 全局变量，该变量为文件 I/O 操作指定默认的*文件提交模式*。  
  
## <a name="syntax"></a>语法  
  
```cpp  
int * __p__commode(  
   );  
```  
  
## <a name="return-value"></a>返回值  
 指向 `_commode` 全局变量的指针。  
  
## <a name="remarks"></a>备注  
 `__p__commode` 函数仅供内部使用，且不应从用户代码调用它。  
  
 文件提交模式指定关键数据写入到磁盘的时间。 有关详细信息，请参阅 [fflush](../c-runtime-library/reference/fflush.md)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|__p\__commode|internal.h|
