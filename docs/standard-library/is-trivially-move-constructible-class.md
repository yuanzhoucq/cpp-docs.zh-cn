---
title: "is_trivially_move_constructible 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- is_trivially_move_constructible
- type_traits/std::is_trivially_move_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_move_constructible
ms.assetid: 740bdec7-65e5-47b3-b94f-a2479ceac3ec
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 51fbd09793071631985720550007dddbe16f598f
ms.openlocfilehash: bfcd131b706f68b6cea38880c3c7fcd49527bba4
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="istriviallymoveconstructible-class"></a>is_trivially_move_constructible 类
测试类型是否具有普通移动构造函数。  
  
## <a name="syntax"></a>语法  
  
```
template <class Ty>
struct is_trivially_move_constructible;
```  
  
#### <a name="parameters"></a>参数  
 `Ty`  
 要查询的类型。  
  
## <a name="remarks"></a>备注  
 如果类型 `Ty` 是一个具有普通移动构造函数的类，则类型谓词的实例为 true，否则为 false。  
  
 如果符合以下条件，则类 `Ty` 的移动构造函数为普通构造函数：  
  
 它被隐式声明  
  
 其参数类型等效于那些隐式声明的参数类型  
  
 类 `Ty` 没有虚函数  
  
 类 `Ty` 没有虚拟基  
  
 类没有任何不稳定的非静态数据成员  
  
 类 `Ty` 的所有直接基均具有普通构造函数  
  
 类类型的所有非静态数据成员的类具有普通构造函数  
  
 类的类型数组的所有非静态数据成员的类具有普通构造函数  
  
## <a name="requirements"></a>要求  
 **标头：**\<type_traits>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [<type_traits>](../standard-library/type-traits.md)




