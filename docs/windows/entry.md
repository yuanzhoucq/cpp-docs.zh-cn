---
title: 条目 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.entry
dev_langs:
- C++
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 933fc1db2a890fedd9d725c49bbeb6c363e2f4c8
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2018
ms.locfileid: "39569633"
---
# <a name="entry"></a>entry
通过标识 DLL 中的入口点，在模块中指定的导出的函数或常量。  
  
## <a name="syntax"></a>语法  
  
```  
[ entry(  
   id  
) ]  
```  
  
#### <a name="parameters"></a>参数  
 *id*  
 入口点的 ID。  
  
## <a name="remarks"></a>备注  
 **条目**c + + 属性具有相同的功能[条目](http://msdn.microsoft.com/library/windows/desktop/aa366815)MIDL 特性。  
  
## <a name="example"></a>示例  
 有关示例，请参阅[idl_module](../windows/idl-module.md)有关的示例用法**条目**。  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|`idl_module` 特性|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [IDL 特性](../windows/idl-attributes.md)   