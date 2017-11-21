---
title: "max_is |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.max_is
dev_langs: C++
helpviewer_keywords: max_is attribute
ms.assetid: 7c851f5c-6649-4d77-a792-247c37d8f560
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 74b5badf3b65ecbc9842202bdc5bcfc31b5b189f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="maxis"></a>max_is
指定有效的数组索引的最大值。  
  
## <a name="syntax"></a>语法  
  
```  
  
      [ max_is(  
   "expression"  
) ]  
```  
  
#### <a name="parameters"></a>参数  
 *表达式*  
 一个或多个 C 语言表达式。 允许空自变量槽。  
  
## <a name="remarks"></a>备注  
 **Max_is** c + + 属性具有相同的功能[max_is](http://msdn.microsoft.com/library/windows/desktop/aa367074) MIDL 特性。  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|字段中`struct`或**联合**、 接口参数、 接口方法|  
|**可重复**|No|  
|**必需的特性**|无|  
|**无效的特性**|**size_is**|  
  
 有关详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="example"></a>示例  
 请参阅[first_is](../windows/first-is.md)有关如何指定数组的一部分的示例。  
  
## <a name="see-also"></a>另请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
 [Typedef、 Enum、 Union 和 Struct 特性](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Parameter 特性](../windows/parameter-attributes.md)   
 [first_is](../windows/first-is.md)   
 [last_is](../windows/last-is.md)   
 [length_is](../windows/length-is.md)   
 [size_is](../windows/size-is.md)   
