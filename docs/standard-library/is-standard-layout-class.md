---
title: "is_standard_layout 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- is_standard_layout
- type_traits/std::is_standard_layout
dev_langs:
- C++
helpviewer_keywords:
- is_standard_layout class
- is_standard_layout
ms.assetid: 15ccf111-f537-45ef-b552-59152a7ba312
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 28baed4badda4f2c1d7e5b20235fe8d40c2a7195
ms.openlocfilehash: 39b7198e020a2c520fb054687a7dadfdd8172826
ms.lasthandoff: 02/24/2017

---
# <a name="isstandardlayout-class"></a>is_standard_layout 类
测试类型是否为标准布局。  
  
## <a name="syntax"></a>语法  
  
```
template <class Ty>
struct is_standard_layout;
```  
  
#### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`Ty`|要查询的类型|  
  
## <a name="remarks"></a>备注  
 如果类型 `Ty` 是具有内存中成员对象的标准布局的类，则此类型谓词的实例为 true；否则为 false。  
  
## <a name="requirements"></a>要求  
 **标头：**\<type_traits>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [<type_traits>](../standard-library/type-traits.md)




