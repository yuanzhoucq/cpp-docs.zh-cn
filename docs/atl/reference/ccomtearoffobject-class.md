---
title: "CComTearOffObject Class | Microsoft Docs"
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
  - "ATL::CComTearOffObject<Base>"
  - "ATL::CComTearOffObject"
  - "ATL.CComTearOffObject"
  - "ATL.CComTearOffObject<Base>"
  - "CComTearOffObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComTearOffObject class"
  - "tear-off interfaces"
  - "tear-off interfaces, ATL"
ms.assetid: d974b598-c6b2-42b1-8360-9190d9d0fbf3
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComTearOffObject Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类实现一拖曳接口。  
  
## 语法  
  
```  
  
      template<  
   class Base   
>  
class CComTearOffObject :  
   public Base  
```  
  
#### 参数  
 `Base`  
 您的拖曳选件类，从派生 `CComTearOffObjectBase`，您希望接口拖曳对象支持。  
  
 而 `CComTearOffObject` 实现 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)，ATL在两个阶段中实现其拖曳接口\( `CComTearOffObjectBase` 方法处理引用计数和 `QueryInterface`。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CComTearOffObject::CComTearOffObject](../Topic/CComTearOffObject::CComTearOffObject.md)|构造函数。|  
|[CComTearOffObject::~CComTearOffObject](../Topic/CComTearOffObject::~CComTearOffObject.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComTearOffObject::AddRef](../Topic/CComTearOffObject::AddRef.md)|增加 `CComTearOffObject` 对象的引用计数。|  
|[CComTearOffObject::QueryInterface](../Topic/CComTearOffObject::QueryInterface.md)|返回指向在拖曳选件类或所有者选件类的请求的接口。|  
|[CComTearOffObject::Release](../Topic/CComTearOffObject::Release.md)|递减 `CComTearOffObject` 对象的引用计数并销毁它。|  
  
### CComTearOffObjectBase方法  
  
|||  
|-|-|  
|[CComTearOffObjectBase](../Topic/CComTearOffObject::CComTearOffObjectBase.md)|构造函数。|  
  
### CComTearOffObjectBase数据成员  
  
|||  
|-|-|  
|[m\_pOwner](../Topic/CComTearOffObject::m_pOwner.md)|为 `CComObject` 的指针从所有者选件类派生的。|  
  
## 备注  
 `CComTearOffObject` 实现一拖曳接口作为实例化的一个单独的对象，仅当该接口。查询时。  其引用计数成为零时，拖曳被删除。  通常，生成很少使用接口的一拖曳接口，因为使用拖曳保存到您的主要目的所有实例的vtable指针。  
  
 应从 `CComTearOffObjectBase` 派生来实现拖曳的选件类，并从接口希望请拖曳对象支持。  `CComTearOffObjectBase` 在所有者选件类和线程模型templatized。  所有者选件类是拖曳实现对象的选件类。  如果不指定线程模型，则使用默认线程模型。  
  
 您应创建自己的COM映射拖曳选件类。  当ATL实例化拖曳，它将创建 **CComTearOffObject\<CYourTearOffClass\>** 或 **CComCachedTearOffObject\<CYourTearOffClass\>**。  
  
 例如，在BEEPER示例，`CBeeper2` 选件类是拖曳选件类，并 `CBeeper` 选件类是一个所有者选件类:  
  
 [!code-cpp[NVC_ATL_COM#43](../../atl/codesnippet/CPP/ccomtearoffobject-class_1.h)]  
  
## 继承层次结构  
 `Base`  
  
 `CComTearOffObject`  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [CComCachedTearOffObject Class](../../atl/reference/ccomcachedtearoffobject-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)