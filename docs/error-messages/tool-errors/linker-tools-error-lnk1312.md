---
title: "链接器工具错误 LNK1312 | Microsoft Docs"
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
  - "LNK1312"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1312"
ms.assetid: 48284abb-d849-43fc-ab53-45aded14fd8a
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具错误 LNK1312
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无效或损坏的文件: 无法导入程序集  
  
 生成程序集时，向 **\/ASSEMBLYMODULE** 链接器选项传递了一个用 **\/clr** 编译的文件，而不是模块或程序集。如果将对象文件传递给了 **\/ASSEMBLYMODULE**，则只需将对象直接传递给链接器，而不是传递给 **\/ASSEMBLYMODULE**。  
  
## 示例  
 下面的示例创建 .obj 文件。  
  
```  
// LNK1312.cpp  
// compile with: /clr /LD  
public ref class A {  
public:  
   int i;  
};  
```  
  
## 示例  
 下面的示例生成 LNK1312。  
  
```  
// LNK1312_b.cpp  
// compile with: /clr /LD /link /assemblymodule:LNK1312.obj  
// LNK1312 error expected  
public ref class M {};  
```