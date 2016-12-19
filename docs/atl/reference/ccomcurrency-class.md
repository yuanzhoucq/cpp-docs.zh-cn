---
title: "CComCurrency Class | Microsoft Docs"
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
  - "CComCurrency"
  - "ATL.CComCurrency"
  - "ATL::CComCurrency"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComCurrency class"
ms.assetid: a1c3d10a-bba6-40cc-8bcf-aed9023c8a9e
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComCurrency Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CComCurrency` 具有用于创建和管理 CURRENCY 对象的方法和运算符。  
  
## 语法  
  
```  
  
class CComCurrency  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CComCurrency::CComCurrency](../Topic/CComCurrency::CComCurrency.md)|`CComCurrency` 对象的构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComCurrency::GetCurrencyPtr](../Topic/CComCurrency::GetCurrencyPtr.md)|返回 `m_currency` 数据成员的地址。|  
|[CComCurrency::GetFraction](../Topic/CComCurrency::GetFraction.md)|调用此方法以返回 `CComCurrency` 对象的小数部分。|  
|[CComCurrency::GetInteger](../Topic/CComCurrency::GetInteger.md)|调用此方法以返回 `CComCurrency` 对象的整数部分。|  
|[CComCurrency::Round](../Topic/CComCurrency::Round.md)|调用此方法以将 `CComCurrency` 对象舍入为最接近的整数值。|  
|[CComCurrency::SetFraction](../Topic/CComCurrency::SetFraction.md)|调用此方法以设置 `CComCurrency` 对象的小数部分。|  
|[CComCurrency::SetInteger](../Topic/CComCurrency::SetInteger.md)|调用此方法以设置 `CComCurrency` 对象的整数部分。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CComCurrency::operator \-](../Topic/CComCurrency::operator%20-2.md)|此运算符用于对 `CComCurrency` 对象执行减法。|  
|[CComCurrency::operator \!\=](../Topic/CComCurrency::operator%20!=.md)|比较两个 `CComCurrency` 对象是否相等。|  
|[CComCurrency::operator \*](../Topic/CComCurrency::operator%20*.md)|此运算符用于对 `CComCurrency` 对象执行乘法。|  
|[CComCurrency::operator \*\=](../Topic/CComCurrency::operator%20*=.md)|此运算符用于对 `CComCurrency` 对象执行乘法并对它赋予结果。|  
|[CComCurrency::operator \/](../Topic/CComCurrency::operator%20-1.md)|此运算符用于对 `CComCurrency` 对象执行除法。|  
|[CComCurrency::operator \/\=](../Topic/CComCurrency::operator%20-=2.md)|此运算符用于对 `CComCurrency` 对象执行除法并对它赋予结果。|  
|[CComCurrency::operator \+](../Topic/CComCurrency::operator%20+.md)|此运算符用于对 `CComCurrency` 对象执行加法。|  
|[CComCurrency::operator \+\=](../Topic/CComCurrency::operator%20+=.md)|此运算符用于对 `CComCurrency` 对象执行加法并对它赋予结果。|  
|[CComCurrency::operator \<](../Topic/CComCurrency::operator%20%3C.md)|此运算符比较两个 `CComCurrency` 对象以确定较小者。|  
|[CComCurrency::operator \<\=](../Topic/CComCurrency::operator%20%3C=.md)|此运算符比较两个 `CComCurrency` 对象以确定是否相等或较小者。|  
|[CComCurrency::operator \=](../Topic/CComCurrency::operator%20=.md)|此运算符向 `CComCurrency` 对象赋予新值。|  
|[CComCurrency::operator \-\=](../Topic/CComCurrency::operator%20-=1.md)|此运算符用于对 `CComCurrency` 对象执行减法并对它赋予结果。|  
|[CComCurrency::operator \=\=](../Topic/CComCurrency::operator%20==.md)|此运算符比较两个 `CComCurrency` 对象是否相等。|  
|[CComCurrency::operator \>](../Topic/CComCurrency::operator%20%3E.md)|此运算符比较两个 `CComCurrency` 对象以确定较大者。|  
|[CComCurrency::operator \>\=](../Topic/CComCurrency::operator%20%3E=.md)|此运算符比较两个 `CComCurrency` 对象以确定是否相等或较大者。|  
|[CComCurrency::operator CURRENCY](../Topic/CComCurrency::operator%20CURRENCY.md)|强制转换 `CURRENCY` 对象。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CComCurrency::m\_currency](../Topic/CComCurrency::m_currency.md)|由类实例创建的 `CURRENCY` 变量。|  
  
## 备注  
 `CComCurrency` 是 **CURRENCY** 数据类型的包装。  **CURRENCY** 是作为按 10,000 缩放的 8 字节补码整数值实现的。  这产生了一个定点数数字，小数点左侧有 15 位数，右侧有 4 位数。  **CURRENCY** 数据类型对于涉及到货币的计算或精确度至关重要的所有定点数计算非常有用。  
  
 **CComCurrency** 包装实现此定点类型的算术、赋值和比较操作。  已选中受支持的应用程序，以控制定点计算过程中可能出现的舍入误差。  
  
 `CComCurrency` 对象以两个组件的形式提供对小数点两侧的数字的访问权限：一个整数组件，它存储小数点左侧的值；一个小数组件，它存储小数点右侧的值。  小数部分作为介于 \-9999 \(**CY\_MIN\_FRACTION**\) 和 \+9999 \(**CY\_MAX\_FRACTION**\) 之间的整数值存储在内部。  方法 [CComCurrency::GetFraction](../Topic/CComCurrency::GetFraction.md) 返回一个按 10000 \(**CY\_SCALE**\) 倍缩放的值。  
  
 指定 **CComCurrency** 对象的整数和小数部分时，请记住小数部分是 0 到 9999 范围内的数字。  在处理美元等在小数点后仅采用两个有效位数来表示金额的货币时，这一点非常有用。  即使不显示最后两位数字，也必须将它们考虑在内。  
  
|值|可能的 CComCurrency 赋值|  
|-------|-------------------------|  
|$10.50|CComCurrency\(10,5000\) *或* CComCurrency\(10.50\)|  
|$10.05|CComCurrency\(10,500\) *或* CComCurrency\(10.05\)|  
  
 值 **CY\_MIN\_FRACTION**、**CY\_MAX\_FRACTION** 和 **CY\_SCALE** 是在 atlcur.h 中定义的。  
  
## 要求  
 **标头：** atlcur.h  
  
## 请参阅  
 [COleCurrency Class](../../mfc/reference/colecurrency-class.md)   
 [CURRENCY](http://msdn.microsoft.com/zh-cn/5e81273c-7289-45c7-93c0-32c1553f708e)   
 [Class Overview](../../atl/atl-class-overview.md)