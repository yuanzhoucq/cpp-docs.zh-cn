---
title: "CDaoParameterInfo 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDaoParameterInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoParameterInfo 结构"
  - "DAO（数据访问对象）, “参数”集合"
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# CDaoParameterInfo 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“CDaoParameterInfo”  结构包含有关数据访问对象（DAO）定义的参数对象的信息 。  
  
## 语法  
  
```  
  
      struct CDaoParameterInfo  
{  
   CString m_strName;       // Primary  
   short m_nType;           // Primary  
   ColeVariant m_varValue;  // Secondary  
};  
```  
  
#### 参数  
 `m_strName`  
 参数对象唯一名。  有关更多信息，请参见本主题中 DAO 帮助中的“名称属性”。  
  
 `m_nType`  
 指示参数对象的数据类型的值。  有关可能的值的列表，请参见 [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) 结构的 `m_nType` 成员。  有关更多信息，请参见本主题中 DAO 帮助中的“类型属性”。  
  
 *m\_varValue*  
 参数的值中，存储在 [COleVariant](../../mfc/reference/colevariant-class.md) 对象中。  
  
## 备注  
 上述主要的和次要的参考指示信息如何由 `CDaoQueryDef` 类中的 [GetParameterInfo](../Topic/CDaoQueryDef::GetParameterInfo.md) 成员函数返回的。  
  
 MFC 不封装类的 DAO 参数对象。  基础 MFC `CDaoQueryDef` 对象下的 DAO querydef 对象存储它们的参数集合中的参数。  若要访问在 [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) 对象中的参数对象，使用特定参数名或参数集合的索引调用 querydef 对象的 `GetParameterInfo` 成员函数。  可以与 `GetParameterInfo` 一起使用 [CDaoQueryDef::GetParameterCount](../Topic/CDaoQueryDef::GetParameterCount.md) 成员函数来遍历参数集合。  
  
 CDaoQueryDef::GetParameterInfo [](../Topic/CDaoQueryDef::GetParameterInfo.md) 成员函数检索的信息在 `CDaoParameterInfo` 结构中存储。  在使用参数对象存储参数集合的对象上为 querydef 对象调用 `GetParameterInfo` 。  
  
> [!NOTE]
>  如果要只获取或设置的参数值，请使用 `CDaoRecordset` 类的 [GetParamValue](../Topic/CDaoRecordset::GetParamValue.md) 和 [SetParamValue](../Topic/CDaoRecordset::SetParamValue.md) 成员函数。  
  
 `CDaoParameterInfo` 还定义了函数调试版本的 `Dump` 成员。  您可以使用 `Dump` 显示 `CDaoParameterInfo` 对象的内容。  
  
## 要求  
 **头文件：** afxdao.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoQueryDef Class](../../mfc/reference/cdaoquerydef-class.md)