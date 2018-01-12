---
title: "编译器错误 C3106 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3106
dev_langs: C++
helpviewer_keywords: C3106
ms.assetid: 39d97a32-0905-4702-87d3-7f8ce473fb93
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bb90612d2019818ae3f4ba10945c4fd6407e6e50
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3106"></a>编译器错误 C3106
attribute： 未命名自变量必须位于命名的参数之前  
  
 未命名自变量必须传递给之前命名自变量的属性。  
  
 有关详细信息，请参阅 [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3106。  
  
```  
// C3106.cpp  
// compile with: /c  
[module(name="MyLib", dll)];   // C3106  
[module(dll, name="MyLib")];   // OK  
```