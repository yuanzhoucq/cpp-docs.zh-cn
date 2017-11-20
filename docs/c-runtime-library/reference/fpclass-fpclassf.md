---
title: "_fpclass、_fpclassf | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _fpclass
- _fpclassf
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fpclass
- _fpclass
- _fpclassf
- math/_fpclass
- float/_fpclass
- math/_fpclassf
dev_langs: C++
helpviewer_keywords:
- fpclass function
- floating-point numbers, IEEE representation
- _fpclass function
- _fpclassf function
ms.assetid: 2774872d-3543-446f-bc72-db85f8b95a6b
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2e25d66ba7fd25c52758bfb44cc74326c67ce4db
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="fpclass-fpclassf"></a>_fpclass、_fpclassf
返回一个值，该值指示参数的浮点分类。  
  
## <a name="syntax"></a>语法  
  
```  
int _fpclass(   
   double x   
);  
  
int _fpclassf(   
   float x   
); /* x64 only */  
```  
  
#### <a name="parameters"></a>参数  
 `x`  
 要测试的浮点值。  
  
## <a name="return-value"></a>返回值  
 `_fpclass` 和 `_fpclassf` 函数返回一个整数值，该值指示参数 `x` 的浮点分类。 分类可能具有 \<float.h> 中定义的下列值之一。  
  
|值|描述|  
|-----------|-----------------|  
|`_FPCLASS_SNAN`|信令 NaN|  
|`_FPCLASS_QNAN`|静默 NaN|  
|`_FPCLASS_NINF`|负无穷大 (-INF)|  
|`_FPCLASS_NN`|标准化的非零负值|  
|`_FPCLASS_ND`|非标准化的负值|  
|`_FPCLASS_NZ`|负零 （-0）|  
|`_FPCLASS_PZ`|正零 (+0)|  
|`_FPCLASS_PD`|非标准化的正值|  
|`_FPCLASS_PN`|标准化的非零正值|  
|`_FPCLASS_PINF`|正无穷大 (+INF)|  
  
## <a name="remarks"></a>备注  
 `_fpclass` 和 `_fpclassf` 函数是 Microsoft 特定函数。 它们类似于 [fpclassify](../../c-runtime-library/reference/fpclassify.md)，但返回有关参数的更多详情信息。 `_fpclassf` 函数仅在编译 x64 平台时可用。  
  
## <a name="requirements"></a>要求  
  
|函数|必需的标头|  
|--------------|---------------------|  
|`_fpclass`|\<float.h>|  
  
 有关兼容性和符合性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [isnan、_isnan、_isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)   
 [fpclassify](../../c-runtime-library/reference/fpclassify.md)