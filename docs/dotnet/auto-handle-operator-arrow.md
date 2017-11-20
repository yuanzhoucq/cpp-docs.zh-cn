---
title: "auto_handle::operator-&gt; |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- msclr::auto_handle::operator->
- auto_handle.operator->
- auto_handle::operator->
- msclr.auto_handle.operator->
dev_langs: C++
helpviewer_keywords: auto_handle::operator->
ms.assetid: c8c7a771-ea15-41fa-981a-065b8d1162b4
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 06b663caf838c9ee828012fd70f568b5bf456586
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="autohandleoperator-gt"></a>auto_handle::operator-&gt;
成员访问运算符。  
  
## <a name="syntax"></a>语法  
  
```  
_element_type ^ operator->();  
```  
  
## <a name="return-value"></a>返回值  
 由包装的对象`auto_handle`。  
  
## <a name="example"></a>示例  
  
```  
// msl_auto_handle_op_arrow.cpp  
// compile with: /clr  
#include <msclr\auto_handle.h>  
  
using namespace System;  
using namespace msclr;  
  
ref class ClassA {  
protected:     
   String^ m_s;  
public:  
   ClassA( String^ s ) : m_s( s ) {}  
  
   virtual void PrintHello() {  
      Console::WriteLine( "Hello from {0} A!", m_s );  
   }  
  
   int m_i;  
};  
  
int main() {  
   auto_handle<ClassA> a( gcnew ClassA( "first" ) );  
   a->PrintHello();  
  
   a->m_i = 5;  
   Console::WriteLine( "a->m_i = {0}", a->m_i );  
}  
```  
  
```Output  
Hello from first A!  
a->m_i = 5  
```  
  
## <a name="requirements"></a>要求  
 **标头文件** \<msclr\auto_handle.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>另请参阅  
 [auto_handle 成员](../dotnet/auto-handle-members.md)   
 [auto_handle::get](../dotnet/auto-handle-get.md)