---
title: auto_gcroot::swap |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr.auto_gcroot.swap
- msclr::auto_gcroot::swap
- auto_gcroot::swap
- auto_gcroot.swap
dev_langs:
- C++
helpviewer_keywords:
- auto_gcroot::swap
ms.assetid: 4915c629-6a53-432c-8155-3a7511dc70cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 785480c10aff65d02280a9338e79e76cd430a57b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098077"
---
# <a name="autogcrootswap"></a>auto_gcroot::swap
交换与另一个对象`auto_gcroot`。  
  
## <a name="syntax"></a>语法  
  
```  
void swap(  
   auto_gcroot<_element_type> & _right  
);  
```  
  
#### <a name="parameters"></a>参数  
*（_r)*<br/>
`auto_gcroot`要与其交换对象。  
  
## <a name="example"></a>示例  
  
```  
// msl_auto_gcroot_swap.cpp  
// compile with: /clr  
#include <msclr\auto_gcroot.h>  
  
using namespace System;  
using namespace msclr;  
  
int main() {  
   auto_gcroot<String^> s1 = "string one";  
   auto_gcroot<String^> s2 = "string two";  
  
   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",  
      s1->ToString(), s2->ToString() );  
   s1.swap( s2 );  
   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",  
      s1->ToString(), s2->ToString() );  
}  
```  
  
```Output  
s1 = 'string one', s2 = 'string two'  
s1 = 'string two', s2 = 'string one'  
```  
  
## <a name="requirements"></a>要求  
 **标头文件** \<msclr\auto_gcroot.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>请参阅  
 [auto_gcroot 成员](../dotnet/auto-gcroot-members.md)   
 [swap 函数 (auto_gcroot)](../dotnet/swap-function-auto-gcroot.md)