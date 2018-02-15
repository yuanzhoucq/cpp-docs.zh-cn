---
title: "or_eq | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
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
- std::or_eq
- or_eq
- std.or_eq
dev_langs:
- C++
helpviewer_keywords:
- or_eq function
ms.assetid: 1eb92464-ed58-40d8-a30e-f0a6aa2f4318
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 661708d93d79c0fd7be5e54b61044f38c21b1944
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="oreq"></a>or_eq
&#124;= 运算符的替代项。  
  
## <a name="syntax"></a>语法  
  
```  
  
#define or_eq |=  
  
```  
  
## <a name="remarks"></a>备注  
 该宏产生运算符 &#124;=。  
  
## <a name="example"></a>示例  
  
```  
// iso646_oreq.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <iso646.h>  
  
int main( )  
{  
   using namespace std;  
   int a = 3, b = 2, result;  
  
   result= a |= b;  
   cout << result << endl;  
  
   result= a or_eq b;  
   cout << result << endl;  
}  
```  
  
```Output  
3  
3  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<iso646.h>