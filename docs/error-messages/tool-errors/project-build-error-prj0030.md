---
title: "项目生成错误 PRJ0030 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0030"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0030"
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 项目生成错误 PRJ0030
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

宏展开错误。计算 $\(macro\) 超过 32 级的递归。  
  
 此错误是由宏中的递归引起的。  例如，如果将“中间目录”属性（请参见[“常规”属性页（项目）](../../ide/general-property-page-project.md)）设置为 $\(IntDir\)，您将得到递归。  
  
 若要解决此错误，请不要按照用宏和属性来定义的宏来定义这些宏或者属性。