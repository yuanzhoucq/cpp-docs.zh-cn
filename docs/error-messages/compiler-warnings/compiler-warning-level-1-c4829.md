---
title: "编译器警告（等级 1）C4829 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4829"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4829"
ms.assetid: 4ffabe2b-2ddc-4c52-8564-d1355c93cfa6
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4829
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

函数 main 的参数可能不正确。请考虑使用“int main\(Platform::Array\<Platform::String^\>^ argv\)”  
  
 某些函数（如 main）不能采用引用类型参数。  虽然编译会成功，但是生成的图像可能不会运行。  
  
 以下示例生成 C4829：  
  
```  
// C4829.cpp  
// compile by using: cl /EHsc /ZW /W4 /c C4829.cpp  
int main(Platform::String ^ s) {}   // C4829  
  
```