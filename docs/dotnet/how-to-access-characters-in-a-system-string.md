---
title: '如何： 访问 system:: string 中的字符 |Microsoft 文档'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- characters [C++], accessing in System::String
- examples [C++], strings
- strings [C++], accessing characters
ms.assetid: cfc89756-aef3-4988-907e-fb236dcb7087
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ed9682492eedc915919758d42d5594560cb4a83a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-access-characters-in-a-systemstring"></a>如何：访问 System::String 中的字符
你可以访问的字符<xref:System.String>对象到非托管的高性能调用函数采用`wchar_t*`字符串。 该方法生成的第一个字符的内部指针<xref:System.String>对象。 此指针可以直接操作或固定和传递给需要一个普通函数`wchar_t`字符串。  
  
## <a name="example"></a>示例  
 `PtrToStringChars` 返回<xref:System.Char>，这是内部指针 (也称为`byref`)。 在这种情况下，它是进行垃圾回收。 你无需将固定此指针，除非你要将其传递给本机函数。  
  
 考虑下列代码。  因为不需要固定`ppchar`内部指针，并且如果垃圾回收器移动它指向的字符串，它也将更新`ppchar`。 而无需[pin_ptr (C + + /cli CLI)](../windows/pin-ptr-cpp-cli.md)，代码将工作，并且不具有潜在的性能问题所致固定。  
  
 如果你通过`ppchar`给本机函数，则它必须是钉住指针; 垃圾回收器将不能更新任何指针的非托管的堆栈帧上。  
  
```  
// PtrToStringChars.cpp  
// compile with: /clr  
#include<vcclr.h>  
using namespace System;  
  
int main() {  
   String ^ mystring = "abcdefg";  
  
   interior_ptr<const Char> ppchar = PtrToStringChars( mystring );  
  
   for ( ; *ppchar != L'\0'; ++ppchar )  
      Console::Write(*ppchar);  
}  
```  
  
```Output  
abcdefg  
```  
  
## <a name="example"></a>示例  
 此示例显示了需要固定的位置。  
  
```  
// PtrToStringChars_2.cpp  
// compile with: /clr  
#include <string.h>  
#include <vcclr.h>  
// using namespace System;  
  
size_t getlen(System::String ^ s) {  
   // Since this is an outside string, we want to be secure.  
   // To be secure, we need a maximum size.  
   size_t maxsize = 256;  
   // make sure it doesn't move during the unmanaged call  
   pin_ptr<const wchar_t> pinchars = PtrToStringChars(s);  
   return wcsnlen(pinchars, maxsize);  
};  
  
int main() {  
   System::Console::WriteLine(getlen("testing"));  
}  
```  
  
```Output  
7  
```  
  
## <a name="example"></a>示例  
 内部指针具有本机 c + + 指针的所有的属性。 例如，你可以使用它来指导的链接的数据结构并执行插入和删除只使用一个指针：  
  
```  
// PtrToStringChars_3.cpp  
// compile with: /clr /LD  
using namespace System;  
ref struct ListNode {  
   Int32 elem;   
   ListNode ^ Next;  
};  
  
void deleteNode( ListNode ^ list, Int32 e ) {   
   interior_ptr<ListNode ^> ptrToNext = &list;  
   while (*ptrToNext != nullptr) {  
      if ( (*ptrToNext) -> elem == e )  
         *ptrToNext = (*ptrToNext) -> Next;   // delete node  
      else  
         ptrToNext = &(*ptrToNext) -> Next;   // move to next node  
   }  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [使用 C++ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)