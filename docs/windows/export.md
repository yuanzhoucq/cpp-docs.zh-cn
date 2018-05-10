---
title: 导出 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.export
dev_langs:
- C++
helpviewer_keywords:
- export attribute
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 67b71639fc0b7d0039f5665d2cc187191ac14baf
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="export"></a>export
会导致数据结构，用于放置在.idl 文件。  
  
## <a name="syntax"></a>语法  
  
```  
  
[export]  
  
```  
  
## <a name="remarks"></a>备注  
 **导出**c + + 特性将导致放置在.idl 文件，然后，可使其可用于任何语言的二进制兼容格式的类型库中的数据结构。  
  
 不能将应用**导出**属性类，即使此类仅具有公共成员 (等效于`struct`)。  
  
 如果你导出未命名`enum`s 或`struct`s，则会将以开头的给定名称 **__unnamed * * * x*，其中*x*是序列号。  
  
 对导出有效 typedef 是基类型、 结构、 联合、 枚举，或键入标识符。  请参阅[typedef](http://msdn.microsoft.com/library/windows/desktop/aa367287)有关详细信息。  
  
## <a name="example"></a>示例  
 下面的代码演示如何使用**导出**属性：  
  
```  
// cpp_attr_ref_export.cpp  
// compile with: /LD  
[module(name="MyLibrary")];  
  
[export]  
struct MyStruct {  
   int i;  
};  
```  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|**联合**， `typedef`， `enum`， `struct`，或 `interface`|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [编译器特性](../windows/compiler-attributes.md)   
 [Typedef、Enum、Union 和 Struct 特性](../windows/typedef-enum-union-and-struct-attributes.md)   
