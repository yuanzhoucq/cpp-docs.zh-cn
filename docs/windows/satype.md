---
title: satype |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.satype
dev_langs:
- C++
helpviewer_keywords:
- satype attribute
ms.assetid: 1716590b-6bcb-4aba-b1bc-82f7335f02c3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8a5376e0e830654c15dc31522b07ed53af4492bf
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39603389"
---
# <a name="satype"></a>satype
指定的数据类型`SAFEARRAY`结构。  
  
## <a name="syntax"></a>语法  
  
```  
[ satype(  
   data_type  
) ]  
```  
  
### <a name="parameters"></a>参数  
 *data_type*  
 数据类型为`SAFEARRAY`数据结构是作为参数传递给接口方法。  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|接口参数，接口方法|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
## <a name="remarks"></a>备注  
 **Satype** c + + 属性指定的数据类型`SAFEARRAY`。  
  
> [!NOTE]
>  从删除一定程度的间接性`SAFEARRAY`从它在.cpp 文件中的声明方式生成的.idl 文件中的指针。  
  
## <a name="example"></a>示例  
  
```cpp  
// cpp_attr_ref_satype.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="MyModule")];  
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]  
__interface A {  
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);  
};  
```  
  
## <a name="see-also"></a>请参阅  
 [编译器特性](../windows/compiler-attributes.md)   
 [参数特性](../windows/parameter-attributes.md)   
 [方法特性](../windows/method-attributes.md)   
 [id](../windows/id.md)   