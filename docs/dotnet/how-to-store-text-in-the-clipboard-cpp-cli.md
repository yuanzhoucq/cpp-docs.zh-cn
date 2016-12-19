---
title: "如何：将文本存储在剪贴板中 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "剪贴板, 存储文本"
  - "文本, 在剪贴板中存储"
ms.assetid: 9996023f-b700-47ad-8ad9-1ba201eaa5a6
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：将文本存储在剪贴板中 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面的代码示例使用 <xref:System.Windows.Forms> 命名空间中定义的 <xref:System.Windows.Forms.Clipboard> 对象存储字符串。  此对象提供两个成员函数：<xref:System.Windows.Forms.Clipboard.SetDataObject%2A> 和 <xref:System.Windows.Forms.Clipboard.GetDataObject%2A>。  通过将派生自 <xref:System.Object> 的任何对象发送给 <xref:System.Windows.Forms.Clipboard.SetDataObject%2A>，可将数据存储在剪贴板中。  
  
## 示例  
  
```  
// store_clipboard.cpp  
// compile with: /clr  
#using <System.dll>  
#using <System.Drawing.dll>  
#using <System.Windows.Forms.dll>  
  
using namespace System;  
using namespace System::Windows::Forms;  
  
[STAThread] int main()  
{  
   String^ str = "This text is copied into the Clipboard.";  
  
   // Use 'true' as the second argument if  
   // the data is to remain in the clipboard  
   // after the program terminates.  
   Clipboard::SetDataObject(str, true);  
  
   Console::WriteLine("Added text to the Clipboard.");  
  
   return 0;  
}  
```  
  
## 请参阅  
 [如何：从剪贴板中检索文本](../dotnet/how-to-retrieve-text-from-the-clipboard-cpp-cli.md)   
 [Windows 操作](../dotnet/windows-operations-cpp-cli.md)   
 [使用 C\+\+\/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)