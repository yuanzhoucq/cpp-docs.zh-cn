---
title: "com_interface_entry (C++) | Microsoft Docs"
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
  - "vc-attr.com_interface_entry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "com_interface_entry attribute"
ms.assetid: 10368f81-b99b-4a0f-ba4f-a142e6911a5c
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# com_interface_entry (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将接口添加到目标项类中的 COM 映射。  
  
## 语法  
  
```  
  
     [ com_interface_entry(   
  com_interface_entry  
) ]  
```  
  
#### 参数  
 *com\_interface\_entry*  
 包含项的实际的文本字符串。  有关可能值列表，请参见 [COM\_INTERFACE\_ENTRY 宏](../Topic/COM_INTERFACE_ENTRY%20Macros.md)。  
  
## 备注  
 `com_interface_entry` C\+\+ 特性插入字符字符串的非删节的内容到目标对象的 COM 接口映射中。  如果属性一次是应用于目标对象，项插入到现有接口映射的开头。  如果属性重复适用于同一目标对象，接收的项在接口映射开头插入顺序。  
  
 此特性要求 [coclass](../windows/coclass.md)、 [progid](../windows/progid.md)或 [vi\_progid](../windows/vi-progid.md) 属性 \(或表示这些中为\) 的其他特性也适用于同一元素。  如果使用任何单一属性，自动应用其他两个。  例如，因此，如果 **progid** 是应用的，也适用 **vi\_progid** 和 **coclass** 。  
  
 由于 `com_interface_entry` 第一种用法使新接口在接口映射开头插入，它必须是下列 COM\_INTERFACE\_ENTRY 类型之一:  
  
-   COM\_INTERFACE\_ENTRY  
  
-   COM\_INTERFACE\_ENTRY\_IID  
  
-   COM\_INTERFACE\_ENTRY2  
  
-   COM\_INTERFACE\_ENTRY2\_IID  
  
 `com_interface_entry` 属性的其他用法可使用任何支持的 COM\_INTERFACE\_ENTRY 类型。  
  
 ，因为 ATL 在接口映射使用先输入为标识 **IUnknown**，此限制是必需的;因此，项必须是有效的接口。  例如，在中，因为在接口映射的第一个输入不指定实际的 COM 接口，下面的代码示例是无效的。  
  
```  
[ coclass, com_interface_entry =  
    "COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"  
]  
   class CMyClass  
   {  
   };  
```  
  
## 示例  
 下面的代码添加两项。 **CMyBaseClass**现有 COM 接口映射。  第一个是一个标准接口，因此，第二个隐藏 **IDebugTest** 接口。  
  
```  
// cpp_attr_ref_com_interface_entry.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module (name ="ldld")];  
  
[ object,  
  uuid("7dbebed3-d636-4917-af62-c767a720a5b9")]  
__interface IDebugTest{};  
  
[ object,  
  uuid("2875ceac-f94b-4087-8e13-d13dc167fcfc")]  
__interface IMyClass{};  
  
[ coclass,  
  com_interface_entry ("COM_INTERFACE_ENTRY (IMyClass)"),  
  com_interface_entry ("COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"),  
  uuid("b85f8626-e76e-4775-b6a0-4826a9e94af2")  
]  
  
class CMyClass: public IMyClass, public IDebugTest  
{  
};  
```  
  
 **CMyBaseClass** 生成的 COM 对象映射如下所示:  
  
```  
BEGIN_COM_MAP(CMyClass)  
    COM_INTERFACE_ENTRY (IMyClass)  
    COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)  
    COM_INTERFACE_ENTRY(IMyClass)  
    COM_INTERFACE_ENTRY2(IDispatch, IMyClass)  
    COM_INTERFACE_ENTRY(IDebugTest)  
    COM_INTERFACE_ENTRY(IProvideClassInfo)  
END_COM_MAP()  
```  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|**类**， `struct`|  
|**可重复**|是|  
|**必需的特性**|一个或多个以下各项: **coclass**、 **progid**或 **vi\_progid**。|  
|**无效的特性**|无|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [COM Attributes](../windows/com-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)