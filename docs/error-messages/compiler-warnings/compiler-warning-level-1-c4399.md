---
title: "编译器警告 （等级 1） C4399 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4399
dev_langs: C++
helpviewer_keywords: C4399
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: eff01c29d423b0823b41bf63702cf42ee839a523
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4399"></a>编译器警告（等级 1）C4399
symbol： 不应与使用 /clr 进行编译时 __declspec （dllimport） 标记为每个进程的符号： 纯  
  
 **/Clr: pure**编译器选项在 Visual Studio 2015 中已弃用。  
  
 本机映像或有本机和 CLR 构造的映像中的数据未导入到纯映像。 若要解决此警告，编译与**/clr** (不**/clr: pure**) 或删除`__declspec(dllimport)`。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4399。  
  
```  
// C4399.cpp  
// compile with: /clr:pure /doc /W1 /c  
__declspec(dllimport) __declspec(process) extern const int i;   // C4399  
```