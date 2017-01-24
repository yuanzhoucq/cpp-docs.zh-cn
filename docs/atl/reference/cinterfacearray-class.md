---
title: "CInterfaceArray Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CInterfaceArray"
  - "CInterfaceArray"
  - "ATL::CInterfaceArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CInterfaceArray class"
ms.assetid: 1f29cf66-a086-4a7b-b6a8-64f73da39f79
caps.latest.revision: 18
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CInterfaceArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当构造一个数组COM接口指针时，此选件类提供有用的方法。  
  
## 语法  
  
```  
  
      template<  
   class I,  
   const IID* piid = & __uuidof( I )  
>  
class CInterfaceArray : public CAtlArray<  
   ATL::CComQIPtr< I, piid >,  
   CComQIPtrElementTraits< I, piid >  
>  
```  
  
#### 参数  
 `I`  
 指定指针类型的COM接口将存储。  
  
 `piid`  
 为 `I`IID的指针。  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[CInterfaceArray::CInterfaceArray](../Topic/CInterfaceArray::CInterfaceArray.md)|接口数组的构造函数。|  
  
## 备注  
 此选件类为创建一组提供一个构造函数和派生方法COM接口指针。  在需要时，请使用 [CInterfaceList](../../atl/reference/cinterfacelist-class.md) 列表。  
  
 有关更多信息，请参见 [ATL集合选件类](../../atl/atl-collection-classes.md)。  
  
## 继承层次结构  
 `CAtlArray`  
  
 `CInterfaceArray`  
  
## 要求  
 **Header:** atlcoll.h  
  
## 请参阅  
 [CAtlArray Class](../../atl/reference/catlarray-class.md)   
 [CComQIPtr Class](../../atl/reference/ccomqiptr-class.md)   
 [CComQIPtrElementTraits Class](../../atl/reference/ccomqiptrelementtraits-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)