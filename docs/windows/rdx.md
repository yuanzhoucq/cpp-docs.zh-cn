---
title: rdx |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.rdx
dev_langs:
- C++
helpviewer_keywords:
- rdx attribute
ms.assetid: ff8e4312-c1ad-4934-bdaa-86f54409651e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7647ca56e3159564826efa9caf438456b9ae3568
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="rdx"></a>rdx
创建注册表项或修改现有的注册表项。  
  
## <a name="syntax"></a>语法  
  
```  
  
      [ rdx(   
   key,   
   valuename=NULL,   
   regtype   
) ]  
```  
  
#### <a name="parameters"></a>参数  
 `key`  
 创建或打开密钥的名称。  
  
 `valuename`（可选）  
 指定要设置的值字段。 如果键中不存在具有此名称的值字段，将其添加。  
  
 *regtype*  
 正在添加的注册表项的类型。 可以是以下之一：**文本**， **dword**，**二进制**，或`CString`。  
  
## <a name="remarks"></a>备注  
 **Rdx** c + + 属性在创建或修改现有 COM 组件的注册表项。 该属性将 BEGIN_RDX_MAP 宏添加到实现的目标成员的对象。 `RegistryDataExchange`因 BEGIN_RDX_MAP 宏，而插入的函数可以用于注册表和数据成员之间传输数据  
  
 此属性可以与结合使用[组件类](../windows/coclass.md)， [progid](../windows/progid.md)，或[vi_progid](../windows/vi-progid.md)属性或意味着其中一种其他属性。  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|**类**或`struct`成员|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="example"></a>示例  
 以下代码添加到系统描述 CMyClass COM 组件调用 MyValue 注册表项。  
  
```  
// cpp_attr_ref_rdx.cpp  
// compile with: /LD /link /OPT:NOREF  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
  
[module (name="MyLib")];  
  
class CMyClass {  
public:  
   CMyClass() {  
      strcpy_s(m_sz, "SomeValue");  
   }  
  
   [ rdx(key = "HKCR\\MyApp.MyApp.1", valuename = "MyValue", regtype = "text")]   
   char m_sz[256];  
};  
```  
  
## <a name="see-also"></a>请参阅  
 [COM 特性](../windows/com-attributes.md)   
 [registration_script](../windows/registration-script.md)   
