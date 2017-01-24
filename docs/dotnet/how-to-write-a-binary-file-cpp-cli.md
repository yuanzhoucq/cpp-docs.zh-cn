---
title: "如何：编写二进制文件 (C++/CLI) | Microsoft Docs"
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
  - "二进制文件, 在 C++ 中写入"
  - "文件 [C++], binary"
ms.assetid: 35d97ee6-fc7e-4c36-be18-8bbb3b44b3ae
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：编写二进制文件 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面的代码示例演示如何将二进制数据写入文件中。  使用了 <xref:System.IO> 命名空间中的两个类：<xref:System.IO.FileStream> 和 <xref:System.IO.BinaryWriter>。  <xref:System.IO.FileStream> 表示实际文件，而 <xref:System.IO.BinaryWriter> 则提供允许二进制访问的流的接口。  
  
 下面的代码示例写一个包含二进制格式的整数的文件。  可通过 [如何：读取二进制文件](../dotnet/how-to-read-a-binary-file-cpp-cli.md) 中的代码读此文件。  
  
## 示例  
  
```  
// binary_write.cpp  
// compile with: /clr  
#using<system.dll>  
using namespace System;  
using namespace System::IO;  
  
int main()  
{  
   array<Int32>^ data = {1, 2, 3, 10000};  
  
   FileStream^ fs = gcnew FileStream("data.bin", FileMode::Create);  
   BinaryWriter^ w = gcnew BinaryWriter(fs);  
  
   try   
   {  
      Console::WriteLine("writing data to file:");  
      for (int i=0; i<data->Length; i++)  
      {  
         Console::WriteLine(data[i]);  
         w->Write(data[i]);  
      }  
   }  
   catch (Exception^)   
   {  
     Console::WriteLine("data could not be written");  
     fs->Close();  
     return -1;  
   }  
  
   fs->Close();  
   return 0;  
}  
```  
  
## 请参阅  
 [文件和流 I\/O](../Topic/File%20and%20Stream%20I-O.md)   
 [使用 C\+\+\/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)