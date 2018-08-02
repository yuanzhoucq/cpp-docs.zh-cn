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
ms.openlocfilehash: 84035f2007f3c45c33c1dfa342caf5c788580205
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2018
ms.locfileid: "39460914"
---
# <a name="virtual-c"></a>virtual (C++)
**虚拟**关键字声明的虚函数或虚拟基类。  
  
## <a name="syntax"></a>语法  
  
```  
virtual [type-specifiers] member-function-declarator  
virtual [access-specifier] base-class-name  
```  
  
#### <a name="parameters"></a>参数  
 *类型说明符*  
 指定此虚拟成员函数的返回类型。  
  
 *成员函数声明符*  
 声明一个成员函数。  
  
 *访问说明符*  
 为基类，定义的访问级别**公共**，**保护**或**专用**。 可以在之前或之后出现**虚拟**关键字。  
  
 *基本类名*  
 标识一个以前声明的类类型。  
  
## <a name="remarks"></a>备注  
 请参阅[虚函数](../cpp/virtual-functions.md)有关详细信息。  
  
 另请参阅以下关键字：[类](../cpp/class-cpp.md)，[专用](../cpp/private-cpp.md)，[公共](../cpp/public-cpp.md)，以及[受保护的](../cpp/protected-cpp.md)。  
  
## <a name="see-also"></a>请参阅  
 [关键字](../cpp/keywords-cpp.md)