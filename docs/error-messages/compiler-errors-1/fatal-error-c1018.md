---
title: "错误 C1018 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C1018
dev_langs: C++
helpviewer_keywords: C1018
ms.assetid: 2ceb8a99-30b2-4b80-bf42-e9f3305b3c52
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5623d4d2dadf3bf7de36ae7d9ef2f83d5792669c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1018"></a>错误 C1018
意外的 #elif  
  
 `#elif` 指令出现在 `#if`、 `#ifdef`或 `#ifndef` 构造外部。 仅在这些构造之一中使用 `#elif` 。  
  
 下面的示例生成 C1018：  
  
```  
// C1018.cpp  
#elif      // C1018  
#endif  
  
int main() {}  
```  
  
 可能的解决方法：  
  
```  
// C1018b.cpp  
#if 1  
#elif  
#endif  
  
int main() {}  
```