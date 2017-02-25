---
title: "CComCoClass Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComCoClass"
  - "ATL.CComCoClass"
  - "ATL::CComCoClass"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aggregation [C++], aggregation models"
  - "CComCoClass class"
ms.assetid: 67cfefa4-8df9-47fa-ad58-2d1a1ae25762
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CComCoClass Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类用于创建选件类的实例并获取其属性的方法。  
  
## 语法  
  
```  
  
      template<  
   class T,  
   const CLSID* pclsid = &CLSID_NULL  
>  
class CComCoClass  
```  
  
#### 参数  
 `T`  
 您的选件类，从派生 `CComCoClass`。  
  
 *pclsid*  
 对对象的CLSID的指针。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComCoClass::CreateInstance](../Topic/CComCoClass::CreateInstance.md)|（静态）创建选件类和查询的实例接口的。|  
|[CComCoClass::Error](../Topic/CComCoClass::Error.md)|（静态）返回丰富的错误信息到客户端。|  
|[CComCoClass::GetObjectCLSID](../Topic/CComCoClass::GetObjectCLSID.md)|（静态）返回对象的类标识符。|  
|[CComCoClass::GetObjectDescription](../Topic/CComCoClass::GetObjectDescription.md)|（返回对象的声明的静态\)重写。|  
  
## 备注  
 `CComCoClass` 为检索对象的CLSID，设置错误信息并创建选件类的实例提供方法。  应从派生 `CComCoClass`在 [对象映射](http://msdn.microsoft.com/zh-cn/b57619cc-534f-4b8f-bfd4-0c12f937202f) 任何注册的选件类。  
  
 `CComCoClass` 还定义了默认选件类工厂和摘要设计您的对象的。  `CComCoClass` 使用以下两种宏:  
  
-   [DECLARE\_CLASSFACTORY](../Topic/DECLARE_CLASSFACTORY.md) 声明选件类工厂是 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md)。  
  
-   [DECLARE\_AGGREGATABLE](../Topic/DECLARE_AGGREGATABLE.md) 声明您的对象可以聚合。  
  
 通过指定另一个宏重写这些默认之一在类定义中。  例如，使用 [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) 而不是 `CComClassFactory`，请指定 [DECLARE\_CLASSFACTORY2](../Topic/DECLARE_CLASSFACTORY2.md) 宏:  
  
 [!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/CPP/ccomcoclass-class_1.h)]  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)