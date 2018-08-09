---
title: 用例 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.case
dev_langs:
- C++
helpviewer_keywords:
- case attribute
ms.assetid: 6fb883c3-0526-4932-a901-b4564dcaeb7d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ddccbc1fcecafe5ac924098a344cfb7592ce2116
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647822"
---
# <a name="case-c"></a>case (C++)
用于[switch_type](../windows/switch-type.md)属性中**union**。  
  
## <a name="syntax"></a>语法  
  
```cpp  
[ case(  
   value  
) ]  
```  
  
#### <a name="parameters"></a>参数  
 *value*  
 你想要提供的处理可能输入的值。 类型**值**可以是以下类型之一：  
  
-   `int`  
  
-   `char`  
  
-   `boolean`  
  
-   `enum`  
  
 或此类类型的标识符。  
  
## <a name="remarks"></a>备注  
 **用例**c + + 属性具有相同的功能**用例**MIDL 特性。 此属性仅用于[switch_type](../windows/switch-type.md)属性。  
  
## <a name="example"></a>示例  
 下面的代码演示的一种用法**用例**属性：  
  
```cpp  
// cpp_attr_ref_case.cpp  
// compile with: /LD  
#include <unknwn.h>  
[export]  
struct SizedValue2 {  
   [switch_type(char), switch_is(kind)] union {  
      [case(1), string]  
          wchar_t* wval;  
      [default, string]  
          char* val;  
   };  
    char kind;  
};  
[module(name="ATLFIRELib")];  
```  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|成员**类**或**结构**|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
 [Typedef、 Enum、 Union 和 Struct 特性](../windows/typedef-enum-union-and-struct-attributes.md)   
 [类特性](../windows/class-attributes.md)   