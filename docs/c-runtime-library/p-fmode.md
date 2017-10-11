---
title: "__p__fmode |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- __p__fmode
apilocation:
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- __p__fmode
dev_langs:
- C++
helpviewer_keywords:
- __p__fmode
ms.assetid: 1daa1394-81eb-43aa-a71b-4cc6acf3207b
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 0a563385ecd1e773433e053cffbae24403eab6fc
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="pfmode"></a>__p__fmode
指向 `_fmode` 全局变量，该变量为文件 I/O 操作指定默认的*文件转换模式*。  
  
## <a name="syntax"></a>语法  
  
```cpp  
int* __p__fmode(  
   );  
```  
  
## <a name="return-value"></a>返回值  
 指向 `_fmode` 全局变量的指针。  
  
## <a name="remarks"></a>备注  
 `__p__fmode` 函数仅供内部使用，且不应从用户代码调用它。  
  
 文件转换模式为 [_open](../c-runtime-library/reference/open-wopen.md) 和 [_pipe](../c-runtime-library/reference/pipe.md) I/O 操作指定 `binary` 或 `text` 转换。 有关详细信息，请参阅 [_fmode](../c-runtime-library/fmode.md)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|__p\__fmode|stdlib.h|
