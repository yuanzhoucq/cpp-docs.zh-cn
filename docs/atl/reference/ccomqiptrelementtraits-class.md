---
title: "CComQIPtrElementTraits Class | Microsoft Docs"
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
  - "ATL.CComQIPtrElementTraits"
  - "CComQIPtrElementTraits"
  - "ATL::CComQIPtrElementTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComQIPtrElementTraits class"
ms.assetid: 9df9250a-5413-4362-b133-332932a597c4
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComQIPtrElementTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在创建COM接口指针时的集合，此选件类的方法、静态有用功能和的typedef。  
  
## 语法  
  
```  
  
      template<  
   typename I,  
   const IID* piid = & __uuidof( I )   
>   
class CComQIPtrElementTraits : public CDefaultElementTraits<  
   ATL::CComQIPtr< I, piid >  
>  
```  
  
#### 参数  
 `I`  
 指定指针类型的COM接口将存储。  
  
 `piid`  
 为 `I`IID的指针。  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|说明|  
|--------|--------|  
|[CComQIPtrElementTraits::INARGTYPE](../Topic/CComQIPtrElementTraits::INARGTYPE.md)|使用的数据类型对于将元素添加到集合选件类对象。|  
  
## 备注  
 在创建 [CComQIPtr](../../atl/reference/ccomqiptr-class.md) COM接口指针对象时，集合选件类此选件类派生方法并提供有用的typedef。  [CInterfaceArray](../../atl/reference/cinterfacearray-class.md) 和 [CInterfaceList](../../atl/reference/cinterfacelist-class.md) 选件类使用此选件类。  
  
 有关更多信息，请参见 [ATL 集合选件类](../../atl/atl-collection-classes.md)。  
  
## 继承层次结构  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CComQIPtrElementTraits`  
  
## 要求  
 **Header:** atlcoll.h  
  
## 请参阅  
 [CDefaultElementTraits Class](../../atl/reference/cdefaultelementtraits-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)