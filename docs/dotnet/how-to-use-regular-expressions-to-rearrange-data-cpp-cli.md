---
title: "如何：使用正则表达式重新排列数据 (C++/CLI) | Microsoft Docs"
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
  - "数据 [C++], 重新排列"
  - "正则表达式 [C++], 重新排列数据"
ms.assetid: 5f91e777-9471-424e-ba75-dca3d1b49e42
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用正则表达式重新排列数据 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面的代码示例演示如何使用 .NET Framework 正则表达式支持重新排列数据或重新设置数据格式。  下面的代码示例使用 <xref:System.Text.RegularExpressions.Regex> 和 <xref:System.Text.RegularExpressions.Match> 类从字符串中提取第一个名称和最后一个名称，然后按相反顺序显示这些名称元素。  
  
 <xref:System.Text.RegularExpressions.Regex> 类用于构造描述当前数据格式的正则表达式。  假设这两个名称以逗号分隔，并且可以在逗号周围使用任意数量的空白。  然后使用 <xref:System.Text.RegularExpressions.Match> 方法来分析每个字符串。  如果成功，将从 <xref:System.Text.RegularExpressions.Match> 对象中检索第一个和最后一个名称并进行显示。  
  
## 示例  
  
```  
// regex_reorder.cpp  
// compile with: /clr  
#using <System.dll>  
using namespace System;  
using namespace Text::RegularExpressions;  
  
int main()  
{  
   array<String^>^ name =   
   {  
      "Abolrous, Sam",   
      "Berg,Matt",   
      "Berry , Jo",  
      "www.contoso.com"  
   };  
  
   Regex^ reg = gcnew Regex("(?<last>\\w*)\\s*,\\s*(?<first>\\w*)");  
  
   for ( int i=0; i < name->Length; i++ )  
   {  
      Console::Write( "{0,-20}", name[i] );  
      Match^ m = reg->Match( name[i] );  
      if ( m->Success )  
      {  
         String^ first = m->Groups["first"]->Value;  
         String^ last = m->Groups["last"]->Value;  
         Console::WriteLine("{0} {1}", first, last);  
      }  
      else  
         Console::WriteLine("(invalid)");  
   }  
   return 0;  
}  
```  
  
## 请参阅  
 [.NET Framework 正则表达式](../Topic/.NET%20Framework%20Regular%20Expressions.md)   
 [使用 C\+\+\/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)