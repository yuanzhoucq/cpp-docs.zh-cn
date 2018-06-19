---
title: 如何： 使用 Split 方法分析字符串 (C + + /cli CLI) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parsing strings [C++]
- examples [C++], strings
- regular expressions [C++], parsing strings
- Split method, parsing strings
- strings [C++], parsing
ms.assetid: d52d2539-5ebb-4716-86b3-07314dd7e4bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 48c5f26cae67dbfa9feb412917ed3a1d3dc7abbf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33132016"
---
# <a name="how-to-parse-strings-using-the-split-method-ccli"></a>如何：使用 Split 方法分析字符串 (C++/CLI)
下面的代码示例演示如何使用<xref:System.String.Split%2A?displayProperty=fullName>方法从字符串提取每个单词。 包含多个类型的字描绘的字符串进行构造并进行分析通过调用<xref:System.String.Split%2A>描绘的列表。 然后，该句中的每个单词会单独显示。  
  
## <a name="example"></a>示例  
  
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
  
## <a name="see-also"></a>请参阅  
 [.NET Framework 正则表达式](/dotnet/standard/base-types/regular-expressions)   
 [使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)