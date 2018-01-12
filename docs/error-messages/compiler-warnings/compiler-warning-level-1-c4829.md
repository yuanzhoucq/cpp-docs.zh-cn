---
title: "编译器警告 （等级 1） C4829 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4829
dev_langs: C++
helpviewer_keywords: C4829
ms.assetid: 4ffabe2b-2ddc-4c52-8564-d1355c93cfa6
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5d662aaf24526320c0ced706534099d4c94a3c9f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4829"></a>编译器警告（等级 1）C4829
函数 main 的参数可能不正确。 请考虑 intmain (platform:: array\<platform:: string ^ > ^ argv)  
  
 某些函数（如 main）不能采用引用类型参数。 虽然编译会成功，但是生成的图像可能不会运行。  
  
 以下示例生成 C4829：  
  
```  
// C4829.cpp  
// compile by using: cl /EHsc /ZW /W4 /c C4829.cpp  
int main(Platform::String ^ s) {}   // C4829  
  
```