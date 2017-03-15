---
title: "如何：使用 Split 方法分析字符串 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "示例 [C++], 字符串"
  - "分析字符串 [C++]"
  - "正则表达式 [C++], 分析字符串"
  - "Split 方法, 分析字符串"
  - "字符串 [C++], 分析"
ms.assetid: d52d2539-5ebb-4716-86b3-07314dd7e4bd
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 Split 方法分析字符串 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面的代码示例演示如何使用 <xref:System.String.Split%2A?displayProperty=fullName> 方法从字符串中提取每个字。  首先构造包含多种类型的字描绘器的字符串，然后使用一个描绘器列表调用 <xref:System.String.Split%2A> 来分析该字符串。  然后，分别显示句子中的每个字。  
  
## 示例  
  
```  
// regex_split.cpp  
// compile with: /clr  
using namespace System;  
  
int main()  
{  
   String^ delimStr = " ,.:\t";  
   Console::WriteLine( "delimiter : '{0}'", delimStr );  
   array<Char>^ delimiter = delimStr->ToCharArray( );  
   array<String^>^ words;  
   String^ line = "one\ttwo three:four,five six seven";  
  
   Console::WriteLine( "text : '{0}'", line );  
   words = line->Split( delimiter );  
   Console::WriteLine( "Number of Words : {0}", words->Length );  
   for (int word=0; word<words->Length; word++)  
      Console::WriteLine( "{0}", words[word] );  
  
   return 0;  
}  
```  
  
## 请参阅  
 [.NET Framework 正则表达式](../Topic/.NET%20Framework%20Regular%20Expressions.md)   
 [使用 C\+\+\/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)