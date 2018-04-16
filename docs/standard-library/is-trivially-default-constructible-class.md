---
title: "is_trivially_default_constructible 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_default_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_default_constructible
ms.assetid: 653ecd73-909f-4dd8-b95a-d1164d1c2da4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dd0b63b1f088eadf2ba2a253083d0f2878c2b751
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="istriviallydefaultconstructible-class"></a>is_trivially_default_constructible 类
测试类型是否具有普通默认构造函数。  
  
## <a name="syntax"></a>语法  
  
```
template <class Ty>
struct is_trivially_default_constructible;
```  
  
#### <a name="parameters"></a>参数  
 `Ty`  
 要查询的类型。  
  
## <a name="remarks"></a>备注  
 如果类型 `Ty` 是具有普通构造函数的类，则类型谓词的实例为 true；否则为 false。  
  
 类 `Ty` 的默认构造函数为普通构造函数，如果：  
  
-   它是一个隐式声明的默认构造函数  
  
-   类 `Ty` 没有虚函数  
  
-   类 `Ty` 没有虚拟基  
  
-   类 `Ty` 的所有直接基均具有普通构造函数  
  
-   类类型的所有非静态数据成员的类具有普通构造函数  
  
-   类的类型数组的所有非静态数据成员的类具有普通构造函数  
  
## <a name="requirements"></a>惠?  
 **标头：**\<type_traits>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>请参阅  
 [<type_traits>](../standard-library/type-traits.md)



