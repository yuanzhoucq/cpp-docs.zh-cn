---
title: "编译器错误 C2870 | Microsoft Docs"
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
  - "C2870"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2870"
ms.assetid: 80523ee9-1fd3-4dc4-8a77-5083deb99066
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2870
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“name”: 命名空间定义必须出现在文件范围内或紧接着出现在另一命名空间定义内  
  
 错误地定义了命名空间 `name`。  命名空间必须在文件范围（在所有块和类外）内定义或紧接着在另一命名空间定义内定义。  
  
 下面的示例生成 C2870：  
  
```  
// C2870.cpp  
// compile with: /c  
int main() {  
   namespace A { int i; };   // C2870  
}  
```