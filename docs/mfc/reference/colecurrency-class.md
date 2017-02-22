---
title: "COleCurrency Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CURRENCY"
  - "COleCurrency"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleCurrency class"
  - "CURRENCY"
  - "fixed-point numbers"
  - "数字, fixed-point"
ms.assetid: 3a36e345-303f-46fb-a57c-858274378a8d
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# COleCurrency Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封装OLE自动化的 `CURRENCY` 数据类型。  
  
## 语法  
  
```  
class COleCurrency  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleCurrency::COleCurrency](../Topic/COleCurrency::COleCurrency.md)|构造 `COleCurrency` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleCurrency::Format](../Topic/COleCurrency::Format.md)|生成 `COleCurrency` 对象的已格式化的字符串表示形式。|  
|[COleCurrency::GetStatus](../Topic/COleCurrency::GetStatus.md)|获取此 `COleCurrency` 对象的状态（有效性）。|  
|[COleCurrency::ParseCurrency](../Topic/COleCurrency::ParseCurrency.md)|从字符串中读取一个 **CURRENCY** 值并将 `COleCurrency`的值。|  
|[COleCurrency::SetCurrency](../Topic/COleCurrency::SetCurrency.md)|将此 `COleCurrency` 对象的值。|  
|[COleCurrency::SetStatus](../Topic/COleCurrency::SetStatus.md)|设置此 `COleCurrency` 对象的状态（有效性）。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[运算符\=](../Topic/COleCurrency::operator%20=.md)|将一个 `COleCurrency` 值。|  
|[运算符\+ \)，](../Topic/COleCurrency::operator%20+,%20-.md)|添加，减去，并更改 `COleCurrency` 值的符号。|  
|[\+\=运算符，\- \=](../Topic/COleCurrency::operator%20+=,%20-=.md)|从此 `COleCurrency` 对象增加和减少 `COleCurrency` 值。|  
|[\*运算符，\/](../Topic/COleCurrency::operator%20*,%20-.md)|由整数值调用一个 `COleCurrency` 值。|  
|[运算符\*\=，\/\=](../Topic/COleCurrency::operator%20*=,%20-=.md)|由整数值调用此 `COleCurrency` 值。|  
|[运算符\<\<](../Topic/COleCurrency::operator%20%3C%3C,%20%3E%3E.md)|输出到 `CArchive` 或 `CDumpContext`的一个 `COleCurrency` 值。|  
|[运算符\>\>](../Topic/COleCurrency::operator%20%3C%3C,%20%3E%3E.md)|来自的输入 `CArchive`的一 `COleCurrency` 对象。|  
|[运算符货币](../Topic/COleCurrency::operator%20CURRENCY.md)|转换 `COleCurrency` 值转换为 **CURRENCY**。|  
|[运算符\=\=、\<、\<\=等.](../Topic/COleCurrency%20Relational%20Operators.md)|比较两个 `COleCurrency` 值。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[COleCurrency::m\_cur](../Topic/COleCurrency::m_cur.md)|包含此 `COleCurrency` 对象的基础 **CURRENCY**。|  
|[COleCurrency::m\_status](../Topic/COleCurrency::m_status.md)|包含此 `COleCurrency` 对象的状态。|  
  
## 备注  
 **COleCurrency** 没有基类。  
  
 **CURRENCY** 实现为一个8字节，补数缩放10,000的整数值。  这在左侧使具有15个数字的内置小数点小数点和4位数右侧。  **CURRENCY** 数据类型很有用于涉及货币的计算，或对准确性重要的所有定点计算。  它是一个OLE自动化的 `VARIANT` 数据类型的类型。  
  
 **COleCurrency** 还实现此定点类型的一些基本算术运算。  支持的操作选中控件在定点计算过程中，生成的舍入误差。  
  
## 继承层次结构  
 `COleCurrency`  
  
## 要求  
 **Header:** afxdisp.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleVariant Class](../../mfc/reference/colevariant-class.md)