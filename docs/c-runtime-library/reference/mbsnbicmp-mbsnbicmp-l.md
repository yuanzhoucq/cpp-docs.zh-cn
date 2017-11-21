---
title: "_mbsnbicmp、_mbsnbicmp_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbsnbicmp_l
- _mbsnbicmp
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _strnicmp
- _wcsnicmp_l
- _mbsnbicmp
- mbsnbicmp
- mbsnbicmp_l
- _tcsnicmp
- _strnicmp_l
- _tcsnicmp_l
- _wcsnicmp
- _mbsnbicmp_l
dev_langs: C++
helpviewer_keywords:
- _tcsnicmp_l function
- _strnicmp function
- mbsnbicmp_l function
- _wcsnicmp_l function
- _mbsnbicmp function
- _mbsnbicmp_l function
- _tcsnicmp function
- _strnicmp_l function
- mbsnbicmp function
- _wcsnicmp function
ms.assetid: ddb44974-8b0c-42f0-90d0-56c9350bae0c
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6abe7372f42e679264ec501918ad62823ba53ba9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="mbsnbicmp-mbsnbicmpl"></a>_mbsnbicmp、_mbsnbicmp_l
比较两个多字节字符字符串的 `n` 个字节，忽略大小写。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
int _mbsnbicmp(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
```  
  
#### <a name="parameters"></a>参数  
 `string1, string2`  
 要比较的 null 终止的字符串。  
  
 `count`  
 要比较的字节数。  
  
## <a name="return-value"></a>返回值  
 返回值指示子字符串之间的关系。  
  
|返回值|描述|  
|------------------|-----------------|  
|< 0|`string1` 子字符串小于 `string2` 子字符串。|  
|0|`string1` 子字符串等于 `string2` 子字符串。|  
|> 0|`string1` 子字符串大于 `string2` 子字符串。|  
  
 发生错误时，`_mbsnbcmp` 返回 `_NLSCMPERROR`，该返回值是在 String.h 和 Mbstring.h 中定义的。  
  
## <a name="remarks"></a>备注  
 `_mbsnbicmp` 函数最多对 `count` 和 `string1` 的前 `string2` 个字节执行序号比较。 通过将每个字符转换为小写进行比较；`_mbsnbcmp` 是 `_mbsnbicmp` 的区分大小写版本。 如果比较 `count` 个字符之前在任一字符串中到达终止 null 字符，则比较停止。 如果比较 `count` 个字符之前在某一字符串中达到终止 null 字符时两个字符串相等，则较短的字符串较小。  
  
 `_mbsnbicmp` 类似于 `_mbsnicmp`，只不过它按 `count` 个字节（而非按字符）对字符串进行比较。  
  
 两个包含位于 ASCII 表中“Z”和“a”之间的字符（“[”、“\\”、“]”、“^”、“_”和“\`”）的字符串将有不同的比较结果，具体取决于它们的大小写形式。 例如，如果比较采用小写形式（“`ABCDE`”>“`ABCD^`”），则字符串“`abcde`”和“`abcd^`”将以一种方式进行比较，而如果采用大写形式，则采用另一个方式经进行比较（“`ABCDE`”<“`ABCD^`”）。  
  
 `_mbsnbicmp` 根据当前使用的[多字节代码页](../../c-runtime-library/code-pages.md)识别多字节字符序列。 它不受当前区域设置影响。  
  
 如果 `string1` 或 `string2` 为空指针，则 `_mbsnbicmp` 会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则函数将返回 `_NLSCMPERROR`，并且将 `errno` 设置为 `EINVAL`。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tcsnicmp`|`_strnicmp`|`_mbsnbicmp`|`_wcsnicmp`|  
|`_tcsnicmp_l`|`_strnicmp_l`|`_mbsnbicmp_l`|`_wcsnicmp_l`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_mbsnbicmp`|<mbstring.h>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
 请参阅 [_mbsnbcmp、_mbsnbcmp_l](../../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md) 的示例。  
  
## <a name="see-also"></a>另请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [_mbsnbcat、_mbsnbcat_l](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)   
 [_mbsnbcmp、_mbsnbcmp_l](../../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md)   
 [_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)