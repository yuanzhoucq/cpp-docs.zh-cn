---
title: NMAKE 错误 U1070 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1070
dev_langs:
- C++
helpviewer_keywords:
- U1070
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1fe39a5d6f6074596561cd8e32f7b9428bc60f6d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
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