---
title: "is_trivially_default_constructible 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_trivially_default_constructible
dev_langs: C++
helpviewer_keywords: is_trivially_default_constructible
ms.assetid: 653ecd73-909f-4dd8-b95a-d1164d1c2da4
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6b936e6cfa3557591a5be9ec2cafda36920039c3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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



