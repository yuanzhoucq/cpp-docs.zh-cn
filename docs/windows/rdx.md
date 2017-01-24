---
title: "rdx | Microsoft Docs"
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
  - "vc-attr.rdx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rdx attribute"
ms.assetid: ff8e4312-c1ad-4934-bdaa-86f54409651e
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# rdx
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

创建注册表项或修改现有的注册表项。  
  
## 语法  
  
```  
  
      [ rdx(   
   key,   
   valuename=NULL,   
   regtype   
) ]  
```  
  
#### 参数  
 `key`  
 将创建或打开的键的名称。  
  
 `valuename`\(可选\)  
 指定要设置的值字段中。  如果具有该名称的值字段不存在于键，添加。  
  
 *regtype*  
 添加的注册表项的类型。  可为下列值之一: **文本**、 **大小。**、 **二进制**或 `CString`。  
  
## 备注  
 **rdx** C\+\+ 特性创建或修改 COM 组件的现有的注册表项。  添加一 BEGIN\_RDX\_MAP 宏到对象实现目标成员。  `RegistryDataExchange`，因为 BEGIN\_RDX\_MAP 宏注入的函数，可用于传输数据在注册表中数据成员之间  
  
 表示这些中的此属性可与 [coclass](../windows/coclass.md)结合使用、 [progid](../windows/progid.md)或 [vi\_progid](../windows/vi-progid.md) 属性或其他属性。  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|**类** 或 `struct` 成员|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 示例  
 下面的代码将名为 MyValue 的注册表项到描述 CMyClass COM 组件的系统。  
  
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
  
## 请参阅  
 [COM Attributes](../windows/com-attributes.md)   
 [registration\_script](../windows/registration-script.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)