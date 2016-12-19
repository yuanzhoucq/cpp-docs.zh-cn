---
title: "如何：使用正则表达式分析字符串 (C++/CLI) | Microsoft Docs"
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
  - "字符串 [C++], 分析"
ms.assetid: 5b0c7ca3-9bba-4389-a45c-6d373cff91b0
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用正则表达式分析字符串 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面的代码示例演示如何使用 <xref:System.Text.RegularExpressions?displayProperty=fullName> 命名空间中的 <xref:System.Text.RegularExpressions.Regex> 类分析简单的字符串。  首先构造一个包含多种类型的字描绘器的字符串。  然后结合使用 <xref:System.Text.RegularExpressions.Regex> 类和 <xref:System.Text.RegularExpressions.Match> 类来分析该字符串。  然后，分别显示句子中的每个字。  
  
## 示例  
  
```  
// regex_parse.cpp  
// compile with: /clr  
#using <system.dll>  
  
using namespace System;  
using namespace System::Text::RegularExpressions;  
  
int main( )  
{  
   int words = 0;  
   String^ pattern = "[a-zA-Z]*";  
   Console::WriteLine( "pattern : '{0}'", pattern );  
   Regex^ regex = gcnew Regex( pattern );  
  
   String^ line = "one\ttwo three:four,five six  seven";     
   Console::WriteLine( "text : '{0}'", line );  
   for( Match^ match = regex->Match( line );   
        match->Success; match = match->NextMatch( ) )   
   {  
      if( match->Value->Length > 0 )  
      {  
         words++;  
         Console::WriteLine( "{0}", match->Value );  
      }  
   }  
   Console::WriteLine( "Number of Words : {0}", words );  
  
   return 0;  
}  
```  
  
## 请参阅  
 [.NET Framework 正则表达式](../Topic/.NET%20Framework%20Regular%20Expressions.md)   
 [使用 C\+\+\/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)