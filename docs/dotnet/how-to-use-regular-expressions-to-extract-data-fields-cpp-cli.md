---
title: "如何：使用正则表达式提取数据字段 (C++/CLI) | Microsoft Docs"
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
  - "数据 [C++], 从字符串中提取"
  - "格式化的字符串 [C++]"
  - "正则表达式 [C++], 提取数据字段"
  - "字符串 [C++], 提取数据"
ms.assetid: b581d9b6-630e-48fa-94fe-20b0f7b89b06
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用正则表达式提取数据字段 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面的代码示例演示如何使用正则表达式从格式化字符串中提取数据。  下面的代码示例使用 <xref:System.Text.RegularExpressions.Regex> 类指定与电子邮件地址对应的模式。  此模式包括可用于检索每个电子邮件地址的用户和主机名部分的字段标识符。  <xref:System.Text.RegularExpressions.Match> 类用于执行实际的模式匹配。  如果给定的电子邮件地址有效，则将提取并显示用户名和主机名。  
  
## 示例  
  
```  
// Regex_extract.cpp  
// compile with: /clr  
#using <System.dll>  
  
using namespace System;  
using namespace System::Text::RegularExpressions;  
  
int main()  
{  
    array<String^>^ address=  
    {  
        "jay@southridgevideo.com",  
        "barry@adatum.com",  
        "treyresearch.net",  
        "karen@proseware.com"  
    };  
  
    Regex^ emailregex = gcnew Regex("(?<user>[^@]+)@(?<host>.+)");  
  
    for (int i=0; i<address->Length; i++)  
    {  
        Match^ m = emailregex->Match( address[i] );  
        Console::Write("\n{0,25}", address[i]);  
  
        if ( m->Success )   
        {  
            Console::Write("   User='{0}'",   
            m->Groups["user"]->Value);  
            Console::Write("   Host='{0}'",   
            m->Groups["host"]->Value);  
        }  
        else   
            Console::Write("   (invalid email address)");  
        }  
  
    Console::WriteLine("");  
    return 0;  
}  
```  
  
## 请参阅  
 [.NET Framework 正则表达式](../Topic/.NET%20Framework%20Regular%20Expressions.md)   
 [使用 C\+\+\/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)