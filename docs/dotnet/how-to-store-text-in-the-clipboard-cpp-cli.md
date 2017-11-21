---
title: "如何： 将文本存储在剪贴板 (C + + /cli CLI) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- text, storing in Clipboard
- Clipboard, storing text
ms.assetid: 9996023f-b700-47ad-8ad9-1ba201eaa5a6
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 971d87da7045e079e62d2ab3274ddc35ddbffaea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-store-text-in-the-clipboard-ccli"></a>如何：将文本存储在剪贴板中 (C++/CLI)
下面的代码示例使用<xref:System.Windows.Forms.Clipboard>中定义的对象<xref:System.Windows.Forms>命名空间来存储字符串。 此对象提供两个成员函数：<xref:System.Windows.Forms.Clipboard.SetDataObject%2A>和<xref:System.Windows.Forms.Clipboard.GetDataObject%2A>。 数据存储在剪贴板上，通过发送从派生的任何对象<xref:System.Object>到<xref:System.Windows.Forms.Clipboard.SetDataObject%2A>。  
  
## <a name="example"></a>示例  
  
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
  
## <a name="see-also"></a>另请参阅  
 [如何： 检索剪贴板中的文本 (C + + /cli CLI)](../dotnet/how-to-retrieve-text-from-the-clipboard-cpp-cli.md)   
 [Windows 操作 (C + + /cli CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)