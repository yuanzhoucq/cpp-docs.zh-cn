---
title: "is_nothrow_default_constructible 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- is_nothrow_default_constructible
- std.is_nothrow_default_constructible
- std::is_nothrow_default_constructible
- type_traits/std::is_nothrow_default_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_default_constructible
ms.assetid: c576fcc9-5be1-43aa-b93a-64d3f1848887
caps.latest.revision: 21
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
ms.sourcegitcommit: 51fbd09793071631985720550007dddbe16f598f
ms.openlocfilehash: 60850f93178fe05511dedddc680eec1adf46f2c0
ms.lasthandoff: 02/24/2017

---
# <a name="isnothrowdefaultconstructible-class"></a>is_nothrow_default_constructible 类
测试类型是否具有非引发默认构造函数。  
  
## <a name="syntax"></a>语法  
  
```
template <class Ty>
struct is_nothrow_default_constructible;
```  
  
#### <a name="parameters"></a>参数  
 `Ty`  
 要查询的类型。  
  
## <a name="remarks"></a>备注  
 如果类型 `Ty` 具有 nothrow 默认构造函数，类型谓词的实例将保留为 true，否则保留为 false。 类型谓词的实例等效于 `is_nothrow_constructible<Ty>`。  
  
## <a name="requirements"></a>要求  
 **标头：**\<type_traits>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [<type_traits>](../standard-library/type-traits.md)




