---
title: "CD2DSizeF 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxrendertarget/CD2DSizeF"
  - "CD2DSizeF"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DSizeF 类"
ms.assetid: f486a1e1-997d-4286-8cb9-26369dc82055
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# CD2DSizeF 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

D2D1\_SIZE\_F 的包装。  
  
## 语法  
  
```  
class CD2DSizeF : public D2D1_SIZE_F;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CD2DSizeF::CD2DSizeF](../Topic/CD2DSizeF::CD2DSizeF.md)|已重载。  构造一 `D2D1_SIZE_F` 对象的一 `CD2DSizeF` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CD2DSizeF::IsNull](../Topic/CD2DSizeF::IsNull.md)|返回一 `boolean` 表达式的值是否不包含有效的数据\(`null`）。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CD2DSizeF::operator CSize](../Topic/CD2DSizeF::operator%20CSize.md)|转换 `CD2DSizeF` 为 `CSize` 对象。|  
  
## 继承层次结构  
 `D2D1_SIZE_F`  
  
 [CD2DSizeF](../../mfc/reference/cd2dsizef-class.md)  
  
## 要求  
 **标头：** afxrendertarget.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)