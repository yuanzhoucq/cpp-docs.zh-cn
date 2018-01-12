---
title: "编译器错误 C2873 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2873
dev_langs: C++
helpviewer_keywords: C2873
ms.assetid: 7a10036b-400e-4364-bd2f-dcd7370c5e28
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 34c06abc5824f6ac08de88f8c155ed0bba35cf9d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2873"></a>编译器错误 C2873
symbol： 符号不能在 using 声明  
  
 A`using`指令是缺少[命名空间](../../cpp/namespaces-cpp.md)关键字。 这将导致编译器错误地解释为代码[using 声明](../../cpp/using-declaration.md)而不是[using 指令](../../cpp/namespaces-cpp.md#using_directives)。