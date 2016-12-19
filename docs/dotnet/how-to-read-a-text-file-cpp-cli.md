---
title: "如何：读取文本文件 (C++/CLI) | Microsoft Docs"
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
  - "读取文本文件"
  - "文本文件, 读取"
ms.assetid: 80551c01-d769-4b6d-8db7-fd53bde21b62
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：读取文本文件 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面的代码示例演示如何通过使用 <xref:System.IO?displayProperty=fullName> 命名空间中定义的 <xref:System.IO.StreamReader> 类打开一个文本文件并逐行阅读。  使用此类的一个实例打开文本文件，然后使用 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=fullName> 方法对每一行进行检索。  
  
 此代码示例读取名为 textfile.txt 并包含文本的文件。  有关此类文件的信息，请参见 [如何：编写文本文件](../dotnet/how-to-write-a-text-file-cpp-cli.md)。  
  
## 示例  
  
```  
// text_read.cpp  
// compile with: /clr  
#using<system.dll>  
using namespace System;  
using namespace System::IO;  
  
int main()  
{  
   String^ fileName = "textfile.txt";  
   try   
   {  
      Console::WriteLine("trying to open file {0}...", fileName);  
      StreamReader^ din = File::OpenText(fileName);  
  
      String^ str;  
      int count = 0;  
      while ((str = din->ReadLine()) != nullptr)   
      {  
         count++;  
         Console::WriteLine("line {0}: {1}", count, str );  
      }  
   }  
   catch (Exception^ e)  
   {  
      if (dynamic_cast<FileNotFoundException^>(e))  
         Console::WriteLine("file '{0}' not found", fileName);  
      else  
         Console::WriteLine("problem reading file '{0}'", fileName);  
   }  
  
   return 0;  
}  
```  
  
## 请参阅  
 [文件和流 I\/O](../Topic/File%20and%20Stream%20I-O.md)   
 [使用 C\+\+\/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)