---
title: "CD2DSizeU 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CD2DSizeU"
  - "afxrendertarget/CD2DSizeU"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DSizeU 类"
ms.assetid: 6e679ba8-2112-43c3-8275-70b660856f02
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# CD2DSizeU 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

D2D1\_SIZE\_U 的包装。  
  
## 语法  
  
```  
class CD2DSizeU : public D2D1_SIZE_U;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CD2DSizeU::CD2DSizeU](../Topic/CD2DSizeU::CD2DSizeU.md)|已重载。  构造一 `D2D1_SIZE_U` 对象的一 `CD2DSizeU` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CD2DSizeU::IsNull](../Topic/CD2DSizeU::IsNull.md)|返回一 `boolean` 表达式的值是否不包含有效的数据\(`null`）。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CD2DSizeU::operator CSize](../Topic/CD2DSizeU::operator%20CSize.md)|转换 `CD2DSizeU` 为 `CSize` 对象。|  
  
## 继承层次结构  
 `D2D1_SIZE_U`  
  
 [CD2DSizeU](../../mfc/reference/cd2dsizeu-class.md)  
  
## 要求  
 **标头：** afxrendertarget.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)