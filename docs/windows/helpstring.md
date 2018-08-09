---
title: helpstring |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpstring
dev_langs:
- C++
helpviewer_keywords:
- helpstring attribute [C++]
ms.assetid: 0401e905-a63e-4fad-98d0-d1efea111966
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: df452614bfd5ee95a810300809678e28abfbf8ef
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39643155"
---
# <a name="helpstring"></a>helpstring
指定一个字符串，用于描述应用该字符串的元素。  
  
## <a name="syntax"></a>语法  
  
```cpp  
[ helpstring(  
   "string"  
) ]  
```  
  
### <a name="parameters"></a>参数  
 *string*  
 帮助字符串的文本。  
  
## <a name="remarks"></a>备注  
 **Helpstring** c + + 属性具有相同的功能[helpstring](http://msdn.microsoft.com/library/windows/desktop/aa366856) MIDL 特性。  
  
## <a name="example"></a>示例  
 有关示例，请参阅[defaultvalue](../windows/defaultvalue.md)有关如何使用的示例**helpstring**。  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|**接口**， **typedef**，**类**，方法、 属性|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
 [接口特性](../windows/interface-attributes.md)   
 [类特性](../windows/class-attributes.md)   
 [方法特性](../windows/method-attributes.md)   
 [Typedef、 Enum、 Union 和 Struct 特性](../windows/typedef-enum-union-and-struct-attributes.md)   
 [帮助文件](../windows/helpfile.md)   
 [helpcontext](../windows/helpcontext.md)   