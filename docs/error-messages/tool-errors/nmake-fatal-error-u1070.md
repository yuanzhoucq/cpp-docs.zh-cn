---
title: "NMAKE 错误 U1070 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1070
dev_langs: C++
helpviewer_keywords: U1070
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5adf5321c96341cfce633a2329a52360be8a45da
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1070"></a>NMAKE 错误 U1070
宏定义 macroname 中的循环  
  
 在给定的宏的定义包含其定义包含给定的宏的宏。 循环的宏定义均无效。  
  
## <a name="example"></a>示例  
 下面的宏定义  
  
```  
ONE=$(TWO)  
TWO=$(ONE)  
```  
  
 会导致以下错误：  
  
```  
cycle in macro definition 'TWO'  
```