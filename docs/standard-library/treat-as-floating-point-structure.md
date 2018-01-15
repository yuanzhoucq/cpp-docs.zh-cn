---
title: "treat_as_floating_point 结构 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: chrono/std::chrono::treat_as_floating_point
dev_langs: C++
ms.assetid: d0a2161c-bbb2-4924-8961-7568d5ad5434
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1679f6819da685a2c49587d703659b941bf45db6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="treatasfloatingpoint-structure"></a>treat_as_floating_point 结构
指定是否可将 `Rep` 视为浮点类型。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Rep>  
struct treat_as_floating_point : is_floating_point<Rep>;  
```  
  
## <a name="remarks"></a>备注  
 仅当专用化 `treat_as_floating_point<Rep>` 派生自 [true_type](../standard-library/type-traits-typedefs.md#true_type) 时，才可将 `Rep` 视为浮点类型。 此模板类可专用于用户定义的类型。  
  
## <a name="requirements"></a>惠?  
 **标头：** \<chrono >  
  
 **命名空间：**std::chrono  
  
## <a name="see-also"></a>请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono>](../standard-library/chrono.md)

