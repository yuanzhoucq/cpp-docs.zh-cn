---
title: "链接器工具警告 LNK4224 | Microsoft Docs"
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
  - "LNK4224"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4224"
ms.assetid: 8624b70e-0b93-43cf-b457-834d38632d0b
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具警告 LNK4224
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不再支持 option；已将其忽略  
  
 指定并忽略了无效、过时的链接器选项。  
  
 例如，如果 \/comment 指令出现在 .obj 中，则可能出现 LNK4224。  可能已通过 [注释](../../preprocessor/comment-c-cpp.md) 杂注使用否决的 exestr 选项添加了 \/comment 指令。  使用 dumpbin [\/ALL](../../build/reference/all.md) 可查看 .obj 文件中的链接器指令。  
  
 如果可能，请修改 .obj 的源代码并移除杂注。  如果确实忽略此警告，使用 **\/clr:pure** 编译的 .executable 可能不按预期运行。  
  
## 示例  
 下面的示例生成 LNK4224。  
  
```  
// LNK4224.cpp  
// compile with: /c /Zi  
// post-build command: link LNK4224.obj /debug /debugtype:map  
int main () {  
   return 0;  
}  
```