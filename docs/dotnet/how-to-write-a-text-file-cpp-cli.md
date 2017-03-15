---
title: "如何：编写文本文件 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "文件 [C++], 文本"
  - "文本文件, 在 C++ 中写入"
ms.assetid: 39ecdba6-84e0-485c-a202-84cf6d7b8d4a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：编写文本文件 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面的代码示例演示如何创建一个文本文件并使用 <xref:System.IO.StreamWriter> 类向其写入文本，该类在 <xref:System.IO> 命名空间中定义。  <xref:System.IO.StreamWriter> 构造函数获取要创建的文件的名称。  如果存在，则覆盖该文件（除非向第二个 <xref:System.IO.StringWriter> 构造函数参数传递了 True）。  
  
 然后使用 <xref:System.IO.StreamWriter.Write%2A> 和 <xref:System.IO.TextWriter.WriteLine%2A> 函数填充该文件。  
  
## 示例  
  
```  
// text_write.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::IO;  
  
int main()   
{  
   String^ fileName = "textfile.txt";  
  
   StreamWriter^ sw = gcnew StreamWriter(fileName);  
   sw->WriteLine("A text file is born!");  
   sw->Write("You can use WriteLine");  
   sw->WriteLine("...or just Write");  
   sw->WriteLine("and do {0} output too.", "formatted");  
   sw->WriteLine("You can also send non-text objects:");  
   sw->WriteLine(DateTime::Now);  
   sw->Close();  
   Console::WriteLine("a new file ('{0}') has been written", fileName);  
  
   return 0;  
}  
```  
  
## 请参阅  
 [文件和流 I\/O](../Topic/File%20and%20Stream%20I-O.md)   
 [使用 C\+\+\/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)