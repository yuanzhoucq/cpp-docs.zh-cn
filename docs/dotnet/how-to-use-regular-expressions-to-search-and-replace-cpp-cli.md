---
title: "如何： 使用正则表达式进行搜索和替换 (C + + /cli CLI) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- search and replace
- Replace method
- regular expressions [C++], search and replace
ms.assetid: 12fe3e18-fe10-4b25-a221-19dc5eab3821
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f66df471d66a82a565fc5c072757664567d1f25c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-regular-expressions-to-search-and-replace-ccli"></a>如何：使用正则表达式进行搜索和替换 (C++/CLI)
下面的代码示例演示如何正则表达式类<xref:System.Text.RegularExpressions.Regex>可用来执行搜索和替换。 这通过完成<xref:System.Text.RegularExpressions.Regex.Replace%2A>方法。 使用的版本将作为输入的两个字符串： 要修改的字符串和字符串 （如果有） 代替部分要插入到给定模式相匹配<xref:System.Text.RegularExpressions.Regex>对象。  
  
 此代码用字符串中的所有数字都替换下划线 (_)，然后都替换具有空字符串，有效地删除它们。 相同的效果，可在单个步骤中，但是，出于演示目的此处使用两个步骤。  
  
## <a name="example"></a>示例  
  
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
  
## <a name="see-also"></a>请参阅  
 [.NET Framework 正则表达式](/dotnet/standard/base-types/regular-expressions)   
 [使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)