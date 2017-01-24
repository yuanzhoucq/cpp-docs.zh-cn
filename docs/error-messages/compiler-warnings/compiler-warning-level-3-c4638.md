---
title: "编译器警告（等级 3）C4638 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4638"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4638"
ms.assetid: 2c07923a-e103-4e40-bd11-fdfed428a5ec
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 3）C4638
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

XML 文档注释目标：引用未知符号“symbol”  
  
 编译器无法解析符号 \(***symbol***\)。 该符号在编译中必须有效。  
  
 下面的示例生成 C4638：  
  
```  
// C4638.cpp // compile with: /clr /doc /LD /W3 using namespace System; /// Text for class MyClass. public ref class MyClass { public: /// <summary> Text </summary> /// <see cref="aSymbolThatAppearsNowhereInMyProject"/> // Try the following line instead: // /// <see cref="System::Console::WriteLine"/> void MyMethod() {} };   // C4638  
```