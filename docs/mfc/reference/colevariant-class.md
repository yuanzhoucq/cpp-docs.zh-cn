---
title: "COleVariant Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleVariant"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "自动化, 参数类型"
  - "COleVariant class"
  - "VARIANT data type"
ms.assetid: e1b5cd4a-b066-4b9b-b48b-6215ed52d998
caps.latest.revision: 24
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleVariant Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封装 [变量](http://msdn.microsoft.com/zh-cn/e305240e-9e11-4006-98cc-26f4932d2118) 数据类型。  
  
## 语法  
  
```  
class COleVariant : public tagVARIANT  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleVariant::COleVariant](../Topic/COleVariant::COleVariant.md)|构造 `COleVariant` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleVariant::Attach](../Topic/COleVariant::Attach.md)|附加 **VARIANT** 到 `COleVariant`。|  
|[COleVariant::ChangeType](../Topic/COleVariant::ChangeType.md)|更改此 `COleVariant` 不同类型的对象。|  
|[COleVariant::Clear](../Topic/COleVariant::Clear.md)|清除此 `COleVariant` 对象。|  
|[COleVariant::Detach](../Topic/COleVariant::Detach.md)|分离 `COleVariant` 的 **VARIANT** 并返回 **VARIANT**。|  
|[COleVariant::GetByteArrayFromVariantArray](../Topic/COleVariant::GetByteArrayFromVariantArray.md)|从现有不同的数组检索字节数组。|  
|[COleVariant::SetString](../Topic/COleVariant::SetString.md)|将字符串转换为特定类型，通常为ANSI。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[COleVariant::operator LPCVARIANT](../Topic/COleVariant::operator%20LPCVARIANT.md)|转换 `COleVariant` 值转换为 `LPCVARIANT`。|  
|[COleVariant::operator LPVARIANT](../Topic/COleVariant::operator%20LPVARIANT.md)|转换 `COleVariant` 对象转换为 `LPVARIANT`。|  
|[COleVariant::operator \=](../Topic/COleVariant::operator%20=.md)|将一个 `COleVariant` 值。|  
|[COleVariant::operator \=\=](../Topic/COleVariant::operator%20==.md)|比较两个 `COleVariant` 值。|  
|[COleVariant::operator \<\<, \>\>](../Topic/COleVariant::operator%20%3C%3C,%20%3E%3E.md)|输出到 `CArchive` 或 `CDumpContext` 的一个 `COleVariant` 值和来自的输入 `CArchive`的一 `COleVariant` 对象。|  
  
## 备注  
 此数据类型用于OLE自动化。  具体而言，[DISPPARAMS](http://msdn.microsoft.com/zh-cn/a16e5a21-766e-4287-b039-13429aa78f8b) 结构包含指向数组 **VARIANT** 结构。  **DISPPARAMS** framework用来将参数传递到 [IDispatch::Invoke](http://msdn.microsoft.com/zh-cn/964ade8e-9d8a-4d32-bd47-aa678912a54d)。  
  
> [!NOTE]
>  此选件类从 **VARIANT** 不要求。  这意味着可以在需要 **VARIANT**，并 **VARIANT** 结构的数据成员是 `COleVariant`的访问数据成员的参数的 `COleVariant`。  
  
 两个相关的MFC选件类 [COleCurrency](../../mfc/reference/colecurrency-class.md) 和 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 封装变量数据类型 **CURRENCY** \(`VT_CY`\)和 **DATE** \(`VT_DATE`）。  `COleVariant` 选件类DAO类选件广泛使用;为此选件类典型用法，例如 [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) 和 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)参见以下选件类。  
  
 有关更多信息，请参见 [变量](http://msdn.microsoft.com/zh-cn/e305240e-9e11-4006-98cc-26f4932d2118)、 [货币](http://msdn.microsoft.com/zh-cn/5e81273c-7289-45c7-93c0-32c1553f708e)、 [DISPPARAMS](http://msdn.microsoft.com/zh-cn/a16e5a21-766e-4287-b039-13429aa78f8b)和 [IDispatch::Invoke](http://msdn.microsoft.com/zh-cn/964ade8e-9d8a-4d32-bd47-aa678912a54d) 项。[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 有关 `COleVariant` 选件类及其使用的更多信息在OLE自动化，请参见“传递参数在OLE自动化”在该文章 [自动化](../../mfc/automation.md)上。  
  
## 继承层次结构  
 `tagVARIANT`  
  
 `COleVariant`  
  
## 要求  
 **Header:** afxdisp.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)