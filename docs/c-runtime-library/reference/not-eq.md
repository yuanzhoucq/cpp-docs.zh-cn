---
title: "not_eq | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- not_eq
- std::not_eq
- std.not_eq
dev_langs: C++
helpviewer_keywords: not_eq function
ms.assetid: d87ad299-8b50-4393-a57f-06f70e1f23fb
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 55d31bbb9d7823161bd98d76884298f3cc089f4d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="noteq"></a>not_eq
!= 运算符的替代项。  
  
## <a name="syntax"></a>语法  
  
```  
  
#define not_eq !=  
  
```  
  
## <a name="remarks"></a>备注  
 该宏产生运算符 !=。  
  
## <a name="example"></a>示例  
  
```  
// iso646_not_eq.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <iso646.h>  
  
int main( )  
{  
   using namespace std;  
   int a = 0, b = 1;  
  
   if (a != b)  
      cout << "a is not equal to b" << endl;  
  
   if (a not_eq b)  
      cout << "a is not equal to b" << endl;  
}  
```  
  
```Output  
a is not equal to b  
a is not equal to b  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<iso646.h>