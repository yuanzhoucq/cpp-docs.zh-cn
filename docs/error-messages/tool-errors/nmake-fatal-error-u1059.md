---
title: "NMAKE 错误 U1059 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1059
dev_langs: C++
helpviewer_keywords: U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fb9ba98b0f82c158e4e11859e85af72efdbbc244
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1059"></a>NMAKE 错误 U1059
语法错误:} 从属项中缺少  
  
 依赖项的搜索路径未正确指定。 存在的路径或右大括号中的空格 (**}**) 已被省略。  
  
 依赖项的目录规范的语法  
  
 **{**   
 ***目录*} 依赖**  
  
 其中`directories`指定一个或多个路径，每个由分号分隔 (**;**)。 不允许有空格。  
  
 如果部分或全部的搜索路径由宏替换，请确保不存在空格宏扩展中。