---
title: lock::operator = = |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- lock::operator==
- msclr.lock.operator==
- msclr::lock::operator==
- lock.operator==
dev_langs:
- C++
helpviewer_keywords:
- lock::operator==
ms.assetid: 3dcf1e5a-53fc-495d-9df5-d7849a41c36c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 38cefb80b1c4c6969cba976c30383c1499a4968d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048885"
---
# <a name="lockoperator"></a>lock::operator==
相等运算符。  
  
## <a name="syntax"></a>语法  
  
```  
template<class T> bool operator==(  
   T t  
);  
```  
  
#### <a name="parameters"></a>参数  
*t*<br/>
要比较相等的对象。  
  
## <a name="return-value"></a>返回值  
 返回`true`如果`t`锁的对象，相同`false`否则为。  
  
## <a name="example"></a>示例  
  
```  
// msl_lock_op_eq.cpp  
// compile with: /clr  
#include <msclr/lock.h>  
  
using namespace System;  
using namespace System::Threading;  
using namespace msclr;  
  
int main () {  
   Object^ o1 = gcnew Object;  
   lock l1(o1);  
   if (l1 == o1) {  
      Console::WriteLine("Equal!");  
   }  
}  
```  
  
```Output  
Equal!  
```  
  
## <a name="requirements"></a>要求  
 **标头文件** \<msclr\lock.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>请参阅  
 [锁定成员](../dotnet/lock-members.md)   
 [lock::operator!=](../dotnet/lock-operator-inequality.md)