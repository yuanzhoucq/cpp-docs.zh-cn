---
title: 使用正则表达式验证格式 (C + + /cli CLI) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], formatting
- data [C++], formatting
- regular expressions [C++], validating data formatting
ms.assetid: 225775c3-3efc-4734-bde2-1fdf73e3d397
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 59a553ac2d58f9304fce3961aa8212c33b26643a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33129611"
---
# <a name="how-to-use-regular-expressions-to-validate-data-formatting-ccli"></a>如何：使用正则表达式验证数据格式 (C++/CLI)
下面的代码示例演示如何将正则表达式来验证字符串的格式。 在下面的代码示例中，字符串应包含有效的电话号码。 下面的代码示例使用字符串"\d{3}-\d{3}-\d{4}"以指示每个字段表示有效的电话号码。 在字符串中的"d"指示一个数字，并每个"d"后面的参数指示必须存在的数字个数。 在这种情况下，所以需要分离，从而可通过短划线的号码。  
  
## <a name="example"></a>示例  
  
```  
// regex_validate.cpp  
// compile with: /clr  
#using <System.dll>  
  
using namespace System;  
using namespace Text::RegularExpressions;  
  
int main()  
{  
   array<String^>^ number =   
   {  
      "123-456-7890",   
      "444-234-22450",   
      "690-203-6578",   
      "146-893-232",  
      "146-839-2322",  
      "4007-295-1111",   
      "407-295-1111",   
      "407-2-5555",   
   };  
  
   String^ regStr = "^\\d{3}-\\d{3}-\\d{4}$";  
  
   for ( int i = 0; i < number->Length; i++ )  
   {  
      Console::Write( "{0,14}", number[i] );  
  
      if ( Regex::IsMatch( number[i], regStr ) )  
         Console::WriteLine(" - valid");  
      else  
         Console::WriteLine(" - invalid");  
   }  
   return 0;  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [.NET Framework 正则表达式](/dotnet/standard/base-types/regular-expressions)   
 [使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)