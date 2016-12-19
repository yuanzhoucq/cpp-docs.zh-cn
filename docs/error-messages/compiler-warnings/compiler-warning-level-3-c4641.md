---
title: "编译器警告（等级 3）C4641 | Microsoft Docs"
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
  - "C4641"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4641"
ms.assetid: 28fe5c3e-6039-42da-9100-1312b5b15aea
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 3）C4641
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

XML 文档注释含有不明确的交叉引用。  
  
 编译器不能明确地解析引用。  若要消除此警告，请指定明确引用所必须的参数信息。  
  
 有关详细信息，请参阅[XML 文档](../../ide/xml-documentation-visual-cpp.md)。  
  
## 示例  
 下面的示例生成 C4641。  
  
```  
// C4641.cpp  
// compile with: /W3 /doc /clr /c  
  
/// <see cref="f" />   // C4641  
// try the following line instead  
// /// <see cref="f(int)" />  
public ref class GR {  
public:  
   void f( int ) {}  
   void f( char ) {}  
};  
```