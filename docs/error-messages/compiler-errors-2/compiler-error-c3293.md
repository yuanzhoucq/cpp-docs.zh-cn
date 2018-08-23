---
title: 编译器错误 C3293 |Microsoft 文档
ms.custom: ''
ms.date: 07/21/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3293
dev_langs:
- C++
helpviewer_keywords:
- C3293
ms.assetid: b772cf98-52e0-4e24-be23-1f5d87d999ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b195a91825b0f20445b29e330f67810329584db7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33257723"
---
# <a name="compiler-error-c3293"></a>编译器错误 C3293
“accessor”：使用“default”访问“type”类的默认属性（索引器）  
  
 未正确访问索引的属性。  请参阅[如何： 使用属性在 C + + /cli CLI](../../dotnet/how-to-use-properties-in-cpp-cli.md)有关详细信息。  

 **2017 及更高版本的 visual Studio**： 在 Visual Studio 2015 及更早版本中，在某些情况下编译器被错误地识别默认索引器作为默认属性。 有可能通过使用标识符“default”访问该属性来解决这个问题。 在 C++11 中将默认值引入为关键字后，解决方法本身会出现问题。 因此，在 Visual Studio 2017 中，需要解决方法的 Bug 都已修复，现在将“default”用于访问类的默认属性时，编译器会引发错误。
  
## <a name="example"></a>示例  
 下面的示例生成 C3293 在 Visual Studio 2015 及更早版本。  
  
```  
// C3293.cpp  
// compile with: /clr /c  
using namespace System;  
ref class IndexerClass {  
public:  
   // default indexer  
   property int default[int] {  
      int get(int index) { return 0; }  
      void set(int index, int value) {}  
   }  
};  
  
int main() {  
   IndexerClass ^ ic = gcnew IndexerClass;  
   ic->Item[0] = 21;   // C3293 in VS2015 OK in VS2017
   ic->default[0] = 21;   // OK in VS2015 and earlier
  
   String ^s = "Hello";  
   wchar_t wc = s->Chars[0];   // C3293 in VS2015 OK in VS2017
   wchar_t wc2 = s->default[0];   // OK in VS2015 and earlier  
   Console::WriteLine(wc2);  
}  
```