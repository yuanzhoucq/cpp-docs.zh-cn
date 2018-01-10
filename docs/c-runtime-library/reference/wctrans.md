---
title: "wctrans | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: wctrans
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords: wctrans
dev_langs: C++
helpviewer_keywords:
- character codes, wctrans
- characters, codes
- characters, converting
- wctrans function
ms.assetid: 215404bf-6d60-489c-9ae9-880e6b586162
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: babda33f03b29e2b8ccaa9967038c3299c4bc6ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="wctrans"></a>wctrans
确定一组字符代码到另一组之间的映射。  
  
## <a name="syntax"></a>语法  
  
```  
wctrans_t wctrans(  
   const char *property   
);  
```  
  
#### <a name="parameters"></a>参数  
 `property`  
 指定一个有效转换的字符串。  
  
## <a name="return-value"></a>返回值  
 如果当前区域设置的 `LC_CTYPE` 类别未定义其名称与属性字符串 `property` 匹配的映射，则函数将返回零。 否则，它将返回一个适合用作对 [towctrans](../../c-runtime-library/reference/towctrans.md) 的后续调用的第二个参数的非零值。  
  
## <a name="remarks"></a>备注  
 此函数确定一组字符代码到另一组之间的映射。  
  
 以下调用对在所有区域设置中具有相同的行为（但可以定义其他映射，甚至在“C”区域设置中）：  
  
|函数|与以下项相同|  
|--------------|-------------|  
|`tolower(`  `c`  `)`|`towctrans(`  `c` `, wctrans("towlower" ) )`|  
|`towupper(`  `c`  `)`|`towctrans(`  `c` `, wctrans( "toupper" ) )`|  
  
## <a name="requirements"></a>惠?  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`wctrans`|\<wctype.h>|  
  
 有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
  
```  
// crt_wctrans.cpp  
// compile with: /EHsc  
// This example determines a mapping from one set of character  
// codes to another.   
  
#include <wchar.h>  
#include <wctype.h>  
#include <stdio.h>  
#include <iostream>  
  
int main()   
{  
    wint_t c = 'a';  
    printf_s("%d\n",c);  
  
    wctrans_t i = wctrans("toupper");  
    printf_s("%d\n",i);  
  
    wctrans_t ii = wctrans("towlower");  
    printf_s("%d\n",ii);  
  
    wchar_t wc = towctrans(c, i);  
    printf_s("%d\n",wc);  
}  
```  
  
```Output  
97  
1  
0  
65  
```  
  
## <a name="see-also"></a>请参阅  
 [数据转换](../../c-runtime-library/data-conversion.md)   
 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)