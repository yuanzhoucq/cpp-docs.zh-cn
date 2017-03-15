---
title: "is_trivially_move_assignable 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- is_trivially_move_assignable
- std.is_trivially_move_assignable
- std::is_trivially_move_assignable
- type_traits/std::is_trivially_move_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_move_assignable
ms.assetid: 374f7322-0706-4bc1-a1a5-4191d0315e28
caps.latest.revision: 11
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
ms.openlocfilehash: b9d94304c6fbbd925ac3b670dc7665402b521dfd
ms.lasthandoff: 02/24/2017

---
# <a name="istriviallymoveassignable-class"></a>is_trivially_move_assignable 类
测试类型是否具有普通移动赋值运算符。  
  
## <a name="syntax"></a>语法  
  
```
template <class Ty>
struct is_trivially_move_assignable;
```  
  
#### <a name="parameters"></a>参数  
 `Ty`  
 要查询的类型。  
  
## <a name="remarks"></a>备注  
 如果类型 `Ty` 是具有普通移动赋值运算符的类，则类型谓词的实例为 true；否则为 false。  
  
 如果符合以下条件，类 `Ty` 的移动赋值运算符是普通运算符：  
  
 它被隐式提供  
  
 类 `Ty` 没有虚函数  
  
 类 `Ty` 没有虚拟基  
  
 类类型的所有非静态数据成员的类具有普通移动赋值运算符  
  
 类的类型数组的所有非静态数据成员的类具有普通移动赋值运算符  
  
## <a name="requirements"></a>要求  
 **标头：**\<type_traits>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [<type_traits>](../standard-library/type-traits.md)




