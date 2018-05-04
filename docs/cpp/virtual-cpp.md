---
title: 虚拟 （C++） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 909fd3fde92479b2e5407608026cb01ec17fced2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
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
  
## <a name="see-also"></a>请参阅  
 [关键字](../cpp/keywords-cpp.md)