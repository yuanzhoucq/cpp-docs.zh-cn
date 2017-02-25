---
title: "链接器工具错误 LNK1107 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1107"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1107"
ms.assetid: a37a893d-5efa-4eba-8f40-6c5518b4b9d0
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 链接器工具错误 LNK1107
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

文件无效或损坏: 无法在 location 读取  
  
 工具未能读取文件。  重新创建文件。  
  
 LNK1107 也发生，如果尝试通过模块 \(.dll 或 .netmodule 扩展名创建的或链接器\); [\/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)[\/clr:noAssembly](../../build/reference/clr-common-language-runtime-compilation.md) .obj 文件传递。  
  
 如果编译下面的示例：  
  
```  
// LNK1107.cpp  
// compile with: /clr /LD  
public ref class MyClass {  
public:  
   void Test(){}  
};  
```  
  
 然后在命令行上指定 **link LNK1107.dll**，将得到 LNK1107 错误。若要解决该错误，请改为指定 **link LNK1107.obj**。