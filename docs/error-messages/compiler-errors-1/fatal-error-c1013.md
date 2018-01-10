---
title: "错误 C1013 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C1013
dev_langs: C++
helpviewer_keywords: C1013
ms.assetid: 5514a679-efe7-4055-bdd3-5693ca0c332f
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6bdc830c526c7093dcc1219df22a41a096aeaf9a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1013"></a>错误 C1013
编译器限制 : 左括号太多  
  
 表达式在单个表达式中包含太多级别的括号。 简化表达式，或将其分解为多个语句。  
  
 在 Visual C++ 6.0 Service Pack 3 之前，单个表达式中嵌套括号的上限是 59 个。 目前，嵌套括号的上限是 256 个。