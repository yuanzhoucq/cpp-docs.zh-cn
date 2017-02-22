---
title: "CObject Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "基类, MFC 对象"
  - "CObject class"
  - "object classes"
  - "对象 [C++], base class for MFC"
ms.assetid: 95e9acd3-d9eb-4ac0-b52b-ca4a501a7a3a
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CObject Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Microsoft基础选件类库的主体基类。  
  
## 语法  
  
```  
class AFX_NOVTABLE CObject  
```  
  
## 成员  
  
### 受保护的构造函数  
  
|名称|说明|  
|--------|--------|  
|[CObject::CObject](../Topic/CObject::CObject.md)|默认构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CObject::AssertValid](../Topic/CObject::AssertValid.md)|验证此对象的完整性。|  
|[CObject::Dump](../Topic/CObject::Dump.md)|导致此对象诊断转储。|  
|[CObject::GetRuntimeClass](../Topic/CObject::GetRuntimeClass.md)|返回 `CRuntimeClass` 结构与此对象类相对应。|  
|[CObject::IsKindOf](../Topic/CObject::IsKindOf.md)|测试对特定选件类的此对象的关系。|  
|[CObject::IsSerializable](../Topic/CObject::IsSerializable.md)|测试以确定是否可以序列化该对象。|  
|[CObject::Serialize](../Topic/CObject::Serialize.md)|加载或存储对象from\/to存档。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CObject::operator delete](../Topic/CObject::operator%20delete.md)|特定 **delete** 运算符。|  
|[CObject::operator new](../Topic/CObject::operator%20new.md)|特定 **new** 运算符。|  
  
## 备注  
 它作为根效果不仅库选件类\(如 `CFile` 和 `CObList`，而且该的选件类编写。  `CObject` 提供基本服务，包括  
  
-   序列化支持  
  
-   运行时选件类信息  
  
-   对象诊断输出  
  
-   使用集合选件类的兼容性  
  
 请注意 `CObject` 不支持多重继承。  您的派生类只能有一个 `CObject` 基类，并且，该 `CObject` 必须是最左侧的在层次结构。  所允许的，但是，具有结构和非`CObject`\-右侧的多重继承分支的派生类。  
  
 如果您的选件类实现和说明，使用某些选项宏您将注意 `CObject` 从派生的主要好处。  
  
 第一层的宏、 [DECLARE\_DYNAMIC](../Topic/DECLARE_DYNAMIC.md) 和 [IMPLEMENT\_DYNAMIC](../Topic/IMPLEMENT_DYNAMIC.md)、许可证运行时访问类名及其位置。层次结构。  这，反过来，允许有意义诊断转储。  
  
 二级宏，[DECLARE\_SERIAL](../Topic/DECLARE_SERIAL.md) 和 [IMPLEMENT\_SERIAL](../Topic/IMPLEMENT_SERIAL.md)，包括第一层的宏的所有功能，并且，它们使对象“来回“序列化存档”。  
  
 有关通常派生Microsoft基础选件类和C\+\+选件类和使用 `CObject`的信息，请参见 [使用CObject](../../mfc/using-cobject.md) 和 [序列化](../../mfc/serialization-in-mfc.md)。  
  
## 继承层次结构  
 `CObject`  
  
## 要求  
 **Header:** afx.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)