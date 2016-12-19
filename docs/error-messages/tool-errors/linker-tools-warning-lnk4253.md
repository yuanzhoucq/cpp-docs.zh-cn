---
title: "链接器工具警告 LNK4253 | Microsoft Docs"
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
  - "LNK4253"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4253"
ms.assetid: ec7433a9-aa9c-495a-a9f2-075e7bc3e7bc
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具警告 LNK4253
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

节“section1”未合并到“section2”；已合并到“section3”  
  
 链接器检测到多个相互冲突的合并请求。  链接器将忽略其中一个请求。  
  
 遇到一个 **\/MERGE** 选项或指令，但由于先前已使用过 **\/MERGE** 选项或指令（或由于来自链接器的隐式合并），`from` 节已合并到了另一个节中。  
  
 若要解决 LNK4253，请移除其中一个合并请求。  
  
 在面向具有 Visual C\+\+ 的 x86 计算机和 Windows CE 目标（ARM、MIPS、SH4 和 Thumb）时，.CRT 节现在是只读的。  如果您的代码依赖以前的行为（.CRT 节具有可读\/可写性），您可能会看到意外的行为。  
  
 有关详细信息，请参阅  
  
-   [\/MERGE（合并节）](../../build/reference/merge-combine-sections.md)  
  
-   [注释](../../preprocessor/comment-c-cpp.md)  
  
## 示例  
 在下面的示例中，将指示链接器两次合并 `.rdata` 节，但合并到不同的节中。  下面的示例生成 LNK4253。  
  
```  
// LNK4253.cpp  
// compile with: /W1 /link /merge:.rdata=text2  
// LNK4253 expected  
#pragma comment(linker, "/merge:.rdata=.text")  
int main() {}  
```