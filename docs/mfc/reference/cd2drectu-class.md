---
title: "CD2DRectU 类 | Microsoft Docs"
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
  - "CD2DRectU"
  - "afxrendertarget/CD2DRectU"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DRectU 类"
ms.assetid: a62f17d1-011d-4867-8f51-fd7e7c00561d
caps.latest.revision: 18
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CD2DRectU 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`D2D1_RECT_U`的包装。  
  
## 语法  
  
```  
class CD2DRectU : public D2D1_RECT_U;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CD2DRectU::CD2DRectU](../Topic/CD2DRectU::CD2DRectU.md)|已重载。  构造一 `D2D1_RECT_U` 对象的一 `CD2DRectU` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CD2DRectU::IsNull](../Topic/CD2DRectU::IsNull.md)|返回一 `boolean` 表达式的值是否不包含有效的数据\(`null`）。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CD2DRectU::operator CRect](../Topic/CD2DRectU::operator%20CRect.md)|转换 `CD2DRectU` 为 `CRect` 对象。|  
  
## 继承层次结构  
 `D2D1_RECT_U`  
  
 [CD2DRectU](../../mfc/reference/cd2drectu-class.md)  
  
## 要求  
 **标头：** afxrendertarget.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)