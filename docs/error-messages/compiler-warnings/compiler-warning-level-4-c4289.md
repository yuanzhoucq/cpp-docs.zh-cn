---
title: "编译器警告 （等级 4） C4289 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4289
dev_langs: C++
helpviewer_keywords: C4289
ms.assetid: 0dbd2863-4cde-4e16-894b-104a2d5fa724
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 98acda62a984f2625ddc742e309aca7628d9c9f3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4289"></a>编译器警告（等级 4）C4289
使用了非标准扩展 :“var”: 在 for 循环中声明的循环控制变量用在了 for 循环范围外  
  
 使用编译时[/Ze](../../build/reference/za-ze-disable-language-extensions.md)和**/zc: forscope-**中, 声明的变量[为](../../cpp/for-statement-cpp.md)之后使用循环已**为**-循环作用域。  
  
 请参阅[/zc: forscope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)有关如何指定标准行为中的**为**循环也**/Ze**。  
  
 默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。  
  
 下面的示例生成 C4289:  
  
```  
// C4289.cpp  
// compile with: /W4 /Zc:forScope-  
#pragma warning(default:4289)  
int main() {  
   for (int i = 0 ; ; )   // C4289  
      break;  
   i++;  
}  
```