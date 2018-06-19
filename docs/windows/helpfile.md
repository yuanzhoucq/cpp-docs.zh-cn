---
title: helpfile |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpfile
dev_langs:
- C++
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 926d0fec27bf323f559ad2fe0dffbd4208b1bf2a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876184"
---
# <a name="helpfile"></a>helpfile
设置类型库的帮助文件的名称。  
  
## <a name="syntax"></a>语法  
  
```  
  
      [ helpfile(  
   "filename"  
) ]  
```  
  
#### <a name="parameters"></a>参数  
 *filename*  
 包含的帮助主题文件的名称。  
  
## <a name="remarks"></a>备注  
 **Helpfile** c + + 属性具有相同的功能[helpfile](http://msdn.microsoft.com/library/windows/desktop/aa366853) MIDL 特性。  
  
## <a name="example"></a>示例  
 请参阅示例[模块](../windows/module-cpp.md)以举例说明如何使用**helpfile**。  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|`interface``typedef`，**类**，方法、 属性|  
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
 [helpcontext](../windows/helpcontext.md)   
 [helpstring](../windows/helpstring.md)   
