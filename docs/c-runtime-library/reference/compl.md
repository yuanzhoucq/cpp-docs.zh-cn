---
title: "compl | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: compl
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
- std::compl
- std.compl
- compl
dev_langs: C++
helpviewer_keywords: compl function
ms.assetid: e03f6fb5-cb8b-4afa-99c0-905f4105fb34
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 781412309a53c92479fdefb6d26cdd45fd233c36
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compl"></a>compl
~ 运算符的替代项。  
  
## <a name="syntax"></a>语法  
  
```  
  
#define compl ~  
  
```  
  
## <a name="remarks"></a>备注  
 该宏产生运算符 ~。  
  
## <a name="example"></a>示例  
  
```  
// iso646_compl.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <iso646.h>  
  
int main( )  
{  
   using namespace std;  
   int a = 1, result;  
  
   result = ~a;  
   cout << result << endl;  
  
   result= compl(a);  
   cout << result << endl;  
}  
```  
  
```Output  
-2  
-2  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<iso646.h>