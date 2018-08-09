---
title: helpstringcontext |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpstringcontext
dev_langs:
- C++
helpviewer_keywords:
- helpstringcontext attribute [C++]
ms.assetid: d4cd135e-d91c-4aa3-9353-8aeb096f52cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b71d8183921e0df66d6b9a82ff79faf24ccb41d3
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642329"
---
# <a name="helpstringcontext"></a>helpstringcontext
在.hlp 或.chm 文件中指定的帮助主题的 ID。  
  
## <a name="syntax"></a>语法  
  
```cpp  
[ helpstringcontext(  
   contextID  
) ]  
```  
  
### <a name="parameters"></a>参数  
 *contextID*  
 中的 32 位的帮助上下文标识符**帮助**文件。  
  
## <a name="remarks"></a>备注  
 **Helpstringcontext** c + + 属性具有相同的功能[helpstringcontext](http://msdn.microsoft.com/library/windows/desktop/aa366858) ODL 特性。  
  
## <a name="example"></a>示例  
  
```cpp  
// cpp_attr_ref_helpstringcontext.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
  
[   object,   
   helpstring("help string"),   
   helpstringcontext(1),   
   uuid="11111111-1111-1111-1111-111111111111"  
]  
__interface IMyI   
{  
   HRESULT xx();  
};  
```  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|**类**，**接口**，接口方法|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
 [接口特性](../windows/interface-attributes.md)   
 [类特性](../windows/class-attributes.md)   
 [方法特性](../windows/method-attributes.md)   
 [模块](../windows/module-cpp.md)   