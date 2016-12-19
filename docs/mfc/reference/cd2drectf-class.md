---
title: "CD2DRectF 类 | Microsoft Docs"
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
  - "afxrendertarget/CD2DRectF"
  - "CD2DRectF"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DRectF 类"
ms.assetid: 87c12d87-9d18-4a19-ba14-0f51d6b6835a
caps.latest.revision: 18
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CD2DRectF 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`D2D1_RECT_F`的包装。  
  
## 语法  
  
```  
class CD2DRectF : public D2D1_RECT_F;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CD2DRectF::CD2DRectF](../Topic/CD2DRectF::CD2DRectF.md)|已重载。  构造一 `D2D1_RECT_F` 对象的一 `CD2DRectF` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CD2DRectF::IsNull](../Topic/CD2DRectF::IsNull.md)|返回一 `boolean` 表达式的值是否不包含有效的数据\(`null`）。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CD2DRectF::operator CRect](../Topic/CD2DRectF::operator%20CRect.md)|转换 `CD2DRectF` 为 `CRect` 对象。|  
  
## 继承层次结构  
 `D2D1_RECT_F`  
  
 [CD2DRectF](../../mfc/reference/cd2drectf-class.md)  
  
## 要求  
 **标头：** afxrendertarget.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)