---
title: "offsetof 宏 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
f1_keywords: offsetof
dev_langs: C++
helpviewer_keywords:
- structure members, offset
- offsetof macro
ms.assetid: f3b4eb16-a882-4d38-afc9-eebd976a7352
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d99947615f2f24116f3d9b64e94daba60c848ec4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="offsetof-macro"></a>offsetof 宏
检索成员与其父结构的开头之间的偏移量。  
  
## <a name="syntax"></a>语法  
  
```  
  
      size_t offsetof(  
   structName,  
   memberName   
);  
```  
  
#### <a name="parameters"></a>参数  
 *structName*  
 父数据结构的名称。  
  
 `memberName`  
 确定其偏移量的父数据结构中成员的名称。  
  
## <a name="return-value"></a>返回值  
 `offsetof` 返回指定成员与其父数据结构的开头之间的偏移量（以字节为单位）。 它对于位域是未定义的。  
  
## <a name="remarks"></a>备注  
 `offsetof` 宏返回 `memberName` 与由 *structName* 指定的作为类型 `size_t` 的值的结构开头之间的偏移量（以字节为单位）。 您可使用 `struct` 关键字指定类型。  
  
> [!NOTE]
>  `offsetof` 不是函数，无法使用 C 原型描述它。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`offsetof`|\<stddef.h>|  
  
 有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="libraries"></a>库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## <a name="see-also"></a>请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)