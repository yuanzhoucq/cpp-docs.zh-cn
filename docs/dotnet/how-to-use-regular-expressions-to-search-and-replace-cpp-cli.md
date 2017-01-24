---
title: "如何：使用正则表达式进行搜索和替换 (C++/CLI) | Microsoft Docs"
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
  - "正则表达式 [C++], 搜索和替换"
  - "Replace 方法"
  - "搜索和替换"
ms.assetid: 12fe3e18-fe10-4b25-a221-19dc5eab3821
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用正则表达式进行搜索和替换 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面的代码示例演示如何使用正则表达式类 <xref:System.Text.RegularExpressions.Regex> 执行搜索和替换。  可通过使用 <xref:System.Text.RegularExpressions.Regex.Replace%2A> 方法完成此任务。  所用的版本将两个字符串作为输入：要修改的字符串和要插入的字符串，后者取代与为 <xref:System.Text.RegularExpressions.Regex> 对象提供的模式相匹配的节（如果有）。  
  
 此代码用下划线 \(\_\) 替换字符串中的所有数字，然后用空字符串替换下划线，从而有效地将其移除。  执行一个步骤就可以得到相同的效果，但为了演示的目的，在此使用两个步骤。  
  
## 示例  
  
```  
// regex_replace.cpp  
// compile with: /clr  
#using <System.dll>  
using namespace System::Text::RegularExpressions;  
using namespace System;  
  
int main()  
{  
   String^ before = "The q43uick bro254wn f0ox ju4mped";  
   Console::WriteLine("original  : {0}", before);  
  
   Regex^ digitRegex = gcnew Regex("(?<digit>[0-9])");  
   String^ after = digitRegex->Replace(before, "_");  
   Console::WriteLine("1st regex : {0}", after);  
  
   Regex^ underbarRegex = gcnew Regex("_");  
   String^ after2 = underbarRegex->Replace(after, "");  
   Console::WriteLine("2nd regex : {0}", after2);  
  
   return 0;  
}  
```  
  
## 请参阅  
 [.NET Framework 正则表达式](../Topic/.NET%20Framework%20Regular%20Expressions.md)   
 [使用 C\+\+\/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)