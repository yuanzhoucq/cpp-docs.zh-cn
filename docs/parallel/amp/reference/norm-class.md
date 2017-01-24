---
title: "norm 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp_short_vectors/Concurrency::graphics::norm"
dev_langs: 
  - "C++"
ms.assetid: 73002f3d-c25e-4119-bcd3-4c46c9b6abf1
caps.latest.revision: 8
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# norm 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

表示一个规范数。  每个元素都是\[\- 1.0f，1.0f\]范围内的浮点数字。  
  
## 语法  
  
```  
class norm;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[norm::norm 构造函数](../Topic/norm::norm%20Constructor.md)|已重载。  默认构造函数。  初始化为 0.0f。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|规范：运算符\-运算符||  
|规范:：运算符\-\-运算符||  
|规范：操作符 浮点运算符|转换运算符  规范数转换为浮点值。|  
|规范：操作符\*\-运算符||  
|规范：操作符\/\=运算符||  
|规范：操作符\+\+运算符||  
|规范：操作符\+\=运算符||  
|规范：操作符\=运算符||  
|规范：操作符\-\=运算符||  
  
## 继承层次结构  
 `norm`  
  
## 要求  
 **页眉：**amp\_short\_vectors.h  
  
 **命名空间：**Concurrency::graphics  
  
## 请参阅  
 [Concurrency::graphics 命名空间](../../../parallel/amp/reference/concurrency-graphics-namespace.md)