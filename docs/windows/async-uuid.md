---
title: "async_uuid |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.async_uuid
dev_langs: C++
helpviewer_keywords: async_uuid attribute
ms.assetid: 235cb0d7-be58-4dd9-983c-e2a21bbc42c6
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9c3d9fc9afb7a6f65be8ace5fec085db9bd92191
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="asyncuuid"></a>async_uuid
指定指示 MIDL 编译器定义的 COM 接口的同步和异步版本的 UUID。  
  
## <a name="syntax"></a>语法  
  
```  
  
      [async_uuid (  
   uuid  
)]  
```  
  
#### <a name="parameters"></a>参数  
 *uuid*  
 一个标识接口的版本的 UUID。  
  
## <a name="remarks"></a>备注  
 **Async_uuid** c + + 属性具有相同的功能[async_uuid](http://msdn.microsoft.com/library/windows/desktop/aa366735) MIDL 特性。  
  
## <a name="example"></a>示例  
  
```  
// cpp_attr_ref_async_uuid.cpp  
// compile with: /LD  
#include <Windows.h>  
[module(name="Test")];  
[object, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb"),   
async_uuid("e8583106-38fd-487e-912e-4fc8645c677e")]  
__interface ICustom {  
   HRESULT Custom([in] long l, [out, retval] long *pLong);  
};  
```  
  
## <a name="requirements"></a>惠?  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|`interface`|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|**双**，**调度接口**|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
 [接口特性](../windows/interface-attributes.md)   
