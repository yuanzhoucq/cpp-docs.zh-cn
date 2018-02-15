---
title: "isspace、iswspace、_isspace_l、_iswspace_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- iswspace
- _isspace_l
- _iswspace_l
- isspace
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- iswspace
- _istspace
- isspace
dev_langs:
- C++
helpviewer_keywords:
- iswspace function
- isspace function
- _iswspace_l function
- _isspace_l function
- iswspace_l function
- isspace_l function
- _istspace function
- istspace function
ms.assetid: b851e0c0-36bb-4dac-a1a3-533540939035
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5eef3b216ed70bb7fa6a22d02827dec34b44c3b3
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="isspace-iswspace-isspacel-iswspacel"></a>isspace、iswspace、_isspace_l、_iswspace_l
确定整数是否表示空格字符。  
  
## <a name="syntax"></a>语法  
  
```  
int isspace(  
   int c   
);  
int iswspace(  
   wint_t c   
);  
int _isspace_l(  
   int c,  
   _locale_t locale  
);  
int _iswspace_l(  
   wint_t c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>参数  
 `c`  
 要测试的整数。  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 如果 `c` 是空格字符的特定表示形式，则每个例程将返回非零值。 `isspace` 返回一个非零值，如果`c`是空白字符 (为 0x09-0x0D 或 0x20)。 `isspace` 函数的测试条件的结果取决于区域设置的 `LC_CTYPE` 类别设置；有关详细信息，请参阅 [setlocale, _wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 这些不带 `_l` 后缀的函数的版本将当前区域设置用于任何依赖于区域设置的行为；带有 `_l` 后缀的版本与之相同，只不过它们改用传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。  
  
 如果 `c` 是对应于标准空白字符的宽字符，则 `iswspace` 返回非零值。  
  
 如果 `isspace` 不是 EOF 或在范围 0 到 0xFF 内（包含 0 和 0xFF），则 `_isspace_l` 和 `c` 的行为没有定义。 当使用调试 CRT 库并且 `c` 不是这些值中的一个时，函数将引发断言。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|**_** `istspace`|`isspace`|[_ismbcspace](../../c-runtime-library/reference/ismbcgraph-functions.md)|`iswspace`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`isspace`|\<ctype.h 1>|  
|`iswspace`|\<ctype.h 1> 或 \<wchar.h 1>|  
|`_isspace_l`|\<ctype.h>|  
|`_iswspace_l`|\<ctype.h 1> 或 \<wchar.h 1>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>请参阅  
 [字符分类](../../c-runtime-library/character-classification.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [is、isw 例程](../../c-runtime-library/is-isw-routines.md)