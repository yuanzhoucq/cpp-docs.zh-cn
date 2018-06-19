---
title: support_error_info |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.support_error_info
dev_langs:
- C++
helpviewer_keywords:
- support_error_info attribute
ms.assetid: 20a2b55c-4738-4b35-a71d-e5e9c3a7e3bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0c366a379d15e50aabdc3c2157f57f85b6b5b33b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889925"
---
# <a name="supporterrorinfo"></a>support_error_info
实现针对返回详细错误的支持。  
  
## <a name="syntax"></a>语法  
  
```  
  
      [ support_error_info(  
   error_interface=uuid  
) ]  
```  
  
#### <a name="parameters"></a>参数  
 **error_interface**  
 实现 **IErrorInfo**的接口的标识符。  
  
## <a name="remarks"></a>备注  
 **support_error_info** C++ 属性实现针对将目标对象遇到的详细上下文错误返回到客户端的支持。 若要使对象支持错误， **IErrorInfo** 接口的方法必须由对象实现。 有关详细信息，请参阅 [支持 IDispatch 和 IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md)。  
  
 此属性将 [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) 类作为基类添加到目标对象。 这会形成 **ISupportErrorInfo** 的默认实现，可以在单个接口在对象上生成错误时使用。  
  
## <a name="example"></a>示例  
 下面的代码将针对 **ISupportErrorInfo** 接口的默认支持添加到 `CMyClass` 对象。  
  
```  
// cpp_attr_ref_support_error_info.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module (name="mymod")];  
[object, uuid("f0b17d66-dc6e-4662-baaf-76758e09c878")]  
__interface IMyErrors  
{  
};  
  
[ coclass, support_error_info("IMyErrors"),  
  uuid("854dd392-bdc7-4781-8667-8757936f2a4f") ]  
class CMyClass  
{  
};  
```  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|**类**|  
|**可重复**|是|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [COM 特性](../windows/com-attributes.md)   
 [类特性](../windows/class-attributes.md)   
