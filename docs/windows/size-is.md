---
title: size_is |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.size_is
dev_langs:
- C++
helpviewer_keywords:
- size_is attribute
ms.assetid: 70192d09-f6c5-4d52-b3fe-303f8cb10aa5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c7f97bb82f3387e82be5bbf120db4fed9aaa092f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889668"
---
# <a name="sizeis"></a>size_is
指定的内存大小为固定大小的指针分配且大小调整了大小的指针和单字节或多维数组的指针。  
  
## <a name="syntax"></a>语法  
  
```  
  
      [ size_is(  
   "expression"  
) ]  
```  
  
#### <a name="parameters"></a>参数  
 *表达式*  
 调整了大小的指针为分配的内存大小。  
  
## <a name="remarks"></a>备注  
 **Size_is** c + + 属性具有相同的功能[size_is](http://msdn.microsoft.com/library/windows/desktop/aa367164) MIDL 特性。  
  
## <a name="example"></a>示例  
 请参阅示例[first_is](../windows/first-is.md)有关如何指定数组的一部分的示例。  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|字段中`struct`或**联合**、 接口参数、 接口方法|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|**max_is**|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
 [Typedef、 Enum、 Union 和 Struct 特性](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Parameter 特性](../windows/parameter-attributes.md)   
 [first_is](../windows/first-is.md)   
 [last_is](../windows/last-is.md)   
 [max_is](../windows/max-is.md)   
 [length_is](../windows/length-is.md)   
