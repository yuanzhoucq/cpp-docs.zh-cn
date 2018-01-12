---
title: "编译器错误 C3115 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3115
dev_langs: C++
helpviewer_keywords: C3115
ms.assetid: 51726145-9782-4ec9-84b9-286f366d9cbd
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cf60a87b73c497fd69998950519bf7479332e51b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3115"></a>编译器错误 C3115
attribute: 构造上不允许此属性  
  
 属性被应用到了意外的构造。  请参阅[按用法分的特性](../../windows/attributes-by-usage.md)有关详细信息。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3115。  
  
```  
// C3115.cpp  
// compile with: /c  
#include <unknwn.h>  
[module(name="xx")];  
  
[object, helpstringdll(xx.dll), uuid("00000000-0000-0000-0000-000000000001")]   // C3115  
// try the following line instead  
// [object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMyI {  
   HRESULT xx();  
};  
```