---
title: "support_error_info | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.support_error_info"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "support_error_info 特性"
ms.assetid: 20a2b55c-4738-4b35-a71d-e5e9c3a7e3bc
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# support_error_info
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

实现针对返回详细错误的支持。  
  
## 语法  
  
```  
  
[ support_error_info(  
   error_interface=  
uuid  
) ]  
  
```  
  
#### 参数  
 **error\_interface**  
 实现 **IErrorInfo** 的接口的标识符。  
  
## 备注  
 **support\_error\_info** C\+\+ 属性实现针对将目标对象遇到的详细上下文错误返回到客户端的支持。 若要使对象支持错误，**IErrorInfo** 接口的方法必须由对象实现。 有关详细信息，请参阅[支持 IDispatch 和 IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md)。  
  
 此属性将 [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) 类作为基类添加到目标对象。 这会形成 **ISupportErrorInfo** 的默认实现，可以在单个接口在对象上生成错误时使用。  
  
## 示例  
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
  
## 要求  
  
### 特性上下文  
  
|||  
|-|-|  
|**适用对象**|**类**|  
|**可重复**|是|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见[特性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [COM Attributes](../windows/com-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)