---
title: "_tzset | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _tzset
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tzset
dev_langs:
- C++
helpviewer_keywords:
- _tzset function
- time environment variables
- environment variables, setting time
ms.assetid: 3f6ed537-b414-444d-b272-5dd377481930
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 669b7d41234c21c3fb4e9a1a28f6b8d1a33c036b
ms.contentlocale: zh-cn
ms.lasthandoff: 04/04/2017

---
# <a name="tzset"></a>_tzset
设置时间环境变量。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅                  [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
void _tzset( void );  
```  
  
## <a name="remarks"></a>备注  
 `_tzset` 函数使用环境变量 `TZ` 的当前设置将值分配到三个全局变量： `_daylight`、 `_timezone`和 `_tzname`。 [_ftime](../../c-runtime-library/reference/ftime-ftime32-ftime64.md) 和 [localtime](../../c-runtime-library/reference/localtime-localtime32-localtime64.md) 函数使用这些变量以便将协调世界时 (UTC) 更正为本地时间，而 `time` 函数使用这些变量以从系统时间计算 UTC。 使用以下语法设置 `TZ` 环境变量：  
  
 `set` `TZ`=`tzn`[+ &#124; -]`hh`[`:``mm`[`:``ss`] ][`dzn`]  
  
 `tzn`  
 三个字母时区名称，如 PST。 必须指定从本地时间到 UTC 的正确偏移量。  
  
 `hh`  
 UTC 和本地时间之间的差异（以小时为单位）。 (+) 号对于正值可选。  
  
 `mm`  
 分钟。 用冒号 ( `hh` ) 分开`:`。  
  
 `ss`  
 秒。 用冒号 ( `mm` ) 分开`:`。  
  
 `dzn`  
 三字母夏令时区域，如 PDT。 如果夏令时制从不会在本地生效，则在没有 `TZ` 的值的情况下设置 `dzn`。 C 运行时库假设使用美国规则实现夏令时 (DST) 的计算。  
  
> [!NOTE]
>  在计算时间差异的符号时一定要小心。 由于时间差异是从本地时间到 UTC 间（不是相反）的偏移量，因此其符号可能会与你直觉上判断的符号相反。 对于早于 UTC 的时区，时间差异为负；对于晚于 UTC 的时区，时间差异为正。  
  
 例如，若要设置 `TZ` 环境变量使其对应于德国的当前时区，则在命令行上输入以下内容：  
  
```  
set TZ=GST-1GDT  
```  
  
 此命令使用 GST 以指示德国标准时间，假定 UTC 晚于德国时间一小时（即德国时间早于 UTC 一小时），并假定德国遵循夏令时制。  
  
 如果`TZ`未设置值，`_tzset`尝试使用由操作系统指定的时区信息。 在 Windows 操作系统中，此信息在控制面板的日期/时间应用程序中指定。 如果 `_tzset` 无法获取此信息，则它默认使用代表太平洋时区的 PST8PDT。  
  
 基于 `TZ` 环境变量值，调用 `_daylight`时将以下值分配给全局变量 `_timezone`、 `_tzname` 和 `_tzset` ：  
  
|全局变量|说明|默认值|  
|---------------------|-----------------|-------------------|  
|`_daylight`|如果在 `TZ` 设置中指定了夏令时区域则为非零值；否则为 0。|1|  
|`_timezone`|UTC 和当地时间之间的差异（以秒为单位）。|28800（28800 秒等于 8 小时）|  
|`_tzname`[0]|`TZ` 环境变量中时区名称的字符串值；如果尚未设置 `TZ` ，则为空。|PST|  
|`_tzname`[1]|夏令时区域的字符串值；如果夏令时区域在 `TZ` 环境变量中省略则为空。|PDT|  
  
 前表中显示的 `_daylight` 和 `_tzname` 数组默认值对应于“PST8PDT”。 如果 DST 区域在 `TZ` 环境变量中省略，则 `_daylight` 的值为 0，并且 `_ftime`、 `gmtime`和 `localtime` 函数将对其 DST 标志返回 0。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_tzset`|\<time.h>|  
  
 有关详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_tzset.cpp  
// This program uses _tzset to set the global variables  
// named _daylight, _timezone, and _tzname. Since TZ is  
// not being explicitly set, it uses the system time.  
  
#include <time.h>  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
    _tzset();  
    int daylight;  
    _get_daylight( &daylight );  
    printf( "_daylight = %d\n", daylight );  
    long timezone;  
    _get_timezone( &timezone );  
    printf( "_timezone = %ld\n", timezone );  
    size_t s;  
    char tzname[100];  
    _get_tzname( &s, tzname, sizeof(tzname), 0 );  
    printf( "_tzname[0] = %s\n", tzname );  
    exit( 0 );  
}  
```  
  
```Output  
_daylight = 1  
_timezone = 28800  
_tzname[0] = Pacific Standard Time  
```  
  
## <a name="see-also"></a>另请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [asctime、_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime、_localtime32、_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [_utime、_utime32、_utime64、_wutime、_wutime32、_wutime64](../../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md)
