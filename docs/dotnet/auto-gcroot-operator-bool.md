---
title: "auto_gcroot::operator bool |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- auto_gcroot.operator bool
- auto_gcroot::operator bool
- msclr.auto_gcroot.operator bool
- msclr::auto_gcroot::operator bool
- operator bool
dev_langs: C++
helpviewer_keywords: bool operator
ms.assetid: 87d38498-4221-4de8-8d02-c2dd2e6274ec
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 375816231f10545411cfdc359df556163c2c6039
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="autogcrootoperator-bool"></a>auto_gcroot::operator bool
使用的运算符`auto_gcroot`条件表达式中。  
  
## <a name="syntax"></a>语法  
  
```  
operator bool() const;  
```  
  
## <a name="return-value"></a>返回值  
 `true`已包装的对象是否有效，则为`false`否则为。  
  
## <a name="remarks"></a>备注  
 此运算符实际将转换为`_detail_class::_safe_bool`即比更安全`bool`因为它不能转换为整型。  
  
## <a name="example"></a>示例  
  
```  
// msl_auto_gcroot_operator_bool.cpp  
// compile with: /clr  
#include <msclr\auto_gcroot.h>  
  
using namespace System;  
using namespace msclr;  
  
int main() {  
   auto_gcroot<String^> s;  
   if ( s ) Console::WriteLine( "s is valid" );  
   if ( !s ) Console::WriteLine( "s is invalid" );  
   s = "something";  
   if ( s ) Console::WriteLine( "now s is valid" );  
   if ( !s ) Console::WriteLine( "now s is invalid" );  
   s.reset();  
   if ( s ) Console::WriteLine( "now s is valid" );  
   if ( !s ) Console::WriteLine( "now s is invalid" );  
}  
```  
  
```Output  
s is invalid  
now s is valid  
now s is invalid  
```  
  
## <a name="requirements"></a>要求  
 **标头文件** \<msclr\auto_gcroot.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>另请参阅  
 [auto_gcroot 成员](../dotnet/auto-gcroot-members.md)   
 [auto_gcroot::operator!](../dotnet/auto-gcroot-operator-logical-not.md)