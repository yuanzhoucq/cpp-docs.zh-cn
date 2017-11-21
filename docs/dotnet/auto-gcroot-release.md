---
title: "auto_gcroot::release |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- msclr::auto_gcroot::release
- auto_gcroot::release
- auto_gcroot.release
- msclr.auto_gcroot.release
dev_langs: C++
helpviewer_keywords: release method
ms.assetid: 40b253f0-154e-4d79-80a4-ff13199c3ff0
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c8c1c6134f1d92bad3dcf60e6253818a85f1b88b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="autogcrootrelease"></a>auto_gcroot::release
释放该对象从`auto_gcroot`管理。  
  
## <a name="syntax"></a>语法  
  
```  
_element_type release();  
```  
  
## <a name="return-value"></a>返回值  
 发布的对象。  
  
## <a name="example"></a>示例  
  
```  
// msl_auto_gcroot_release.cpp  
// compile with: /clr  
#include <msclr\auto_gcroot.h>  
  
using namespace System;  
using namespace msclr;  
  
ref class ClassA {  
   String^ m_s;  
public:  
   ClassA( String^ s ) : m_s( s ) {  
      Console::WriteLine( "ClassA constructor: " + m_s );  
   }  
   ~ClassA() {  
      Console::WriteLine( "ClassA destructor: " + m_s );  
   }  
  
   void PrintHello() {  
      Console::WriteLine( "Hello from {0} A!", m_s );     
   }  
};  
  
int main()  
{  
   ClassA^ a;  
  
   // create a new scope:  
   {  
      auto_gcroot<ClassA^> agc1 = gcnew ClassA( "first" );  
      auto_gcroot<ClassA^> agc2 = gcnew ClassA( "second" );  
      a = agc1.release();  
   }  
   // agc1 and agc2 go out of scope here  
  
   a->PrintHello();  
  
   Console::WriteLine( "done" );  
}  
```  
  
```Output  
ClassA constructor: first  
ClassA constructor: second  
ClassA destructor: second  
Hello from first A!  
done  
```  
  
## <a name="requirements"></a>要求  
 **标头文件** \<msclr\auto_gcroot.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>另请参阅  
 [auto_gcroot 成员](../dotnet/auto-gcroot-members.md)   
 [auto_gcroot::~auto_gcroot](../dotnet/auto-gcroot-tilde-auto-gcroot.md)