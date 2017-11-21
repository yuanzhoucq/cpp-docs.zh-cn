---
title: "如何： 读取文本文件 (C + + /cli CLI) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- reading text files
- text files, reading
ms.assetid: 80551c01-d769-4b6d-8db7-fd53bde21b62
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 68add197649dd494225787775ab772e8ffc0fc89
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-read-a-text-file-ccli"></a>如何：读取文本文件 (C++/CLI)
下面的代码示例演示如何打开和使用一次读取文本文件的一行<xref:System.IO.StreamReader>中定义的类<xref:System.IO?displayProperty=fullName>命名空间。 此类的实例用于打开一个文本文件，然后<xref:System.IO.StreamReader.ReadLine%2A?displayProperty=fullName>方法用于检索每个行。  
  
 此代码示例读取的文件，具有名为 textfile.txt 并包含文本。 有关这种类型的文件的信息，请参阅[如何： 编写文本文件 (C + + /cli CLI)](../dotnet/how-to-write-a-text-file-cpp-cli.md)。  
  
## <a name="example"></a>示例  
  
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
  
## <a name="see-also"></a>另请参阅  
 [文件和流 I-O](http://msdn.microsoft.com/Library/4f4a33a9-66b7-4cd7-a285-4ad3e4276cd2)   
 [使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)