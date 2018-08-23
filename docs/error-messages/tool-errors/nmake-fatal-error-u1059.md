---
title: NMAKE 错误 U1059 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1059
dev_langs:
- C++
helpviewer_keywords:
- U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6eb038befdb7c587c6fe2a734003abba585c3e2a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320698"
---
# <a name="nmake-fatal-error-u1059"></a>NMAKE 错误 U1059
语法错误:} 从属项中缺少  
  
 依赖项的搜索路径未正确指定。 存在的路径或右大括号中的空格 (**}**) 已被省略。  
  
 依赖项的目录规范的语法  
  
 **{**   
 ***目录*} 依赖**  
  
 其中`directories`指定一个或多个路径，每个由分号分隔 (**;**)。 不允许有空格。  
  
 如果部分或全部的搜索路径由宏替换，请确保不存在空格宏扩展中。