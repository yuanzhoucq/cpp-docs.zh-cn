---
title: "虚拟 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- virtual_cpp
- virtual
dev_langs:
- C++
helpviewer_keywords:
- virtual base classes [C++], declaring
- base classes [C++], virtual
- virtual functions [C++], declaring
- virtual keyword [C++]
ms.assetid: c2eb987d-6cf3-43b6-aa0c-29a6f561b1ae
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 851f911dd7c49df1d685afe63ef5134cf0d5f175
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="virtual-c"></a>virtual (C++)
`virtual` 关键字声明一个虚拟函数或一个虚拟基类。  
  
## <a name="syntax"></a>语法  
  
```  
virtual [type-specifiers] member-function-declarator  
virtual [access-specifier] base-class-name  
```  
  
#### <a name="parameters"></a>参数  
 `type-specifiers`  
 指定此虚拟成员函数的返回类型。  
  
 `member-function-declarator`  
 声明一个成员函数。  
  
 `access-specifier`  
 定义对基类的访问级别（`public`、`protected` 或 `private`）。 可以在 `virtual` 关键字之前或之后显示。  
  
 `base-class-name`  
 标识一个以前声明的类类型。  
  
## <a name="remarks"></a>备注  
 请参阅[虚函数](../cpp/virtual-functions.md)有关详细信息。  
  
 另请参阅以下关键字：[类](../cpp/class-cpp.md)，[私有](../cpp/private-cpp.md)，[公共](../cpp/public-cpp.md)，和[保护](../cpp/protected-cpp.md)。  
  
## <a name="see-also"></a>另请参阅  
 [关键字](../cpp/keywords-cpp.md)
