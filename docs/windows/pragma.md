---
title: "杂注 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.pragma
dev_langs: C++
helpviewer_keywords: pragma attribute
ms.assetid: 3f90d023-b8b5-4007-8311-008bb72cbea1
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9069090fc0d2c405aa31dbf8d0447c28d8e0ef41
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="pragma"></a>pragma
将指定的字符串发出到生成的.idl 文件而不使用引号引起来。 .  
  
## <a name="syntax"></a>语法  
  
```  
  
      [ pragma(  
   pragma_statement  
) ];  
```  
  
#### <a name="parameters"></a>参数  
 *pragma_statement*  
 你想要转到生成的.idl 文件杂注。  
  
## <a name="remarks"></a>备注  
 **杂注**c + + 属性具有相同的功能[杂注](http://msdn.microsoft.com/library/windows/desktop/aa367143)MIDL 特性。  
  
## <a name="example"></a>示例  
  
```  
// cpp_attr_ref_pragma.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="MyLib")];  
[pragma(pack(4))];  
  
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]  
__interface A  
{  
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);  
};  
```  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|任何位置|  
|**可重复**|No|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
 [独立特性](../windows/stand-alone-attributes.md)   
 [pack](../preprocessor/pack.md)   
