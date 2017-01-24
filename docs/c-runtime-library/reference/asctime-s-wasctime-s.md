---
title: "asctime_s、_wasctime_s | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wasctime_s"
  - "asctime_s"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-time-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "asctime_s"
  - "_wasctime_s"
  - "_tasctime_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_tasctime_s 函数"
  - "_wasctime_s 函数"
  - "asctime_s 函数"
  - "tasctime_s 函数"
  - "时间结构转换"
  - "时间, 转换"
  - "wasctime_s 函数"
ms.assetid: 17ad9b2b-a459-465d-976a-42822897688a
caps.latest.revision: 29
caps.handback.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# asctime_s、_wasctime_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

变换一个 `tm` 时间结构为字符串。  这些函数是[asctime、\_wasctime](../../c-runtime-library/reference/asctime-wasctime.md) 的安全增强版本（如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述）。  
  
## 语法  
  
```  
errno_t asctime_s(   
   char* buffer,  
   size_t numberOfElements,  
   const struct tm *_tm   
);  
errno_t _wasctime_s(   
   wchar_t* buffer,  
   size_t numberOfElements  
   const struct tm *_tm   
);  
template <size_t size>  
errno_t asctime_s(   
   char (&buffer)[size],  
   const struct tm *_tm   
); // C++ only  
template <size_t size>  
errno_t _wasctime_s(   
   wchar_t (&buffer)[size],  
   const struct tm *_tm   
); // C++ only  
```  
  
#### 参数  
 `buffer`  
 \[out\] 指向存储结果字符串的缓冲区的指针。  此函数采用了指向具有 `numberOfElements`指定大小的有效的内存位置。  
  
 `numberOfElements`  
 \[in\] 缓冲区大小用于存储结果。  
  
 `_tm`  
 \[in\] 时间\/日期 结构。  此函数采用了指向有效 `struct` 的 `tm` 对象。  
  
## 返回值  
 如果成功,是0。  如果有错误，将调用无效参数处理程序（如[参数验证](../../c-runtime-library/parameter-validation.md)所述）。  如果允许继续执行，返回值是错误代码。  错误代码在ERRNO.H中被定义。  有关详细信息，请参阅[errno 常量](../../c-runtime-library/errno-constants.md)。  下表中显示了每个错误状态返回的实际错误代码。  
  
### 错误情况  
  
|`buffer`|`numberOfElements`|`tm`|返回|`buffer`中的值|  
|--------------|------------------------|----------|--------|-----------------|  
|`NULL`|任意|任意|`EINVAL`|未被修改|  
|不是 `NULL`\(指向有效的内存\)|0|任意|`EINVAL`|未被修改|  
|非 `NULL`|0\< 尺寸 \< 26|任意|`EINVAL`|空字符串|  
|非 `NULL`|\>\= 26|`NULL`|`EINVAL`|空字符串|  
|非 `NULL`|\>\= 26|无效时间结构或不足时组件的值范围|`EINVAL`|空字符串|  
  
> [!NOTE]
>  `wasctime_s` 的错误异常与 `asctime_s` 类似，只是限制字数的标准。  
  
## 备注  
 `asctime` 函数转换为结构存储的时间为字符串。  `_tm` 值通常通过调用 `gmtime` 或 `localtime`获取。  两个函数来填写 `tm` 结构，如 TIME.H. 中定义。  
  
|timeptr 成员|值|  
|----------------|-------|  
|`tm_hour`|午夜后的小时 \(0 – 23\)。|  
|`tm_isdst`|如果夏时制有效，是正值；如果夏时制无效，是0；负值，如果夏时制状态未知，是负值。  C 运行库假设使用美国规则实现夏令时 \(DST\) 的计算。|  
|`tm_mday`|一月中的一天\(1–31\)|  
|`tm_min`|一小时中的分钟 \(0–59\)|  
|`tm_mon`|月份 \(0–11;一月 \= 0\)|  
|`tm_sec`|一分钟的秒数 \(0–59\)|  
|`tm_wday`|一周中的一天 \(0–6;周日 \= 0\)|  
|`tm_yday`|一年中的一天\(0–365; 1 月 1 日 \= 0 \)|  
|`tm_year`|年份 \(当前年份减 1900\)|  
  
 转换的字符串本地根据的时区设置也会调整。  有关环境定义时区和全局变量的信息，请参见、[time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)[\_ftime, \_ftime32, \_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)[localtime\_s, \_localtime32\_s, \_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md) 函数和有关配置本地时间以及 [\_tzset](../../c-runtime-library/reference/tzset.md) 函数的信息。  
  
 `asctime_s` 生成的结果字符串正确包含 26 个字符并具有 `Wed Jan 02 02:03:55 1980\n\0`格式。  使用 24 小时制。  所有字段都具有一个常数的宽度。  换行符和空字符占用字符串中的后两个位置。  将的值作为第二个参数应是至少这大的。  如果小于，错误代码，`EINVAL`，将返回。  
  
 `_wasctime_s` 是 `asctime_s`的宽字符版本。  `_wasctime_s` 和 `asctime_s` 行为相同，否则。  
  
### 通用文本程序映射  
  
|TCHAR.H 例程|未定义的 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|-----------------------------|----------------|-------------------|  
|`_tasctime_s`|`asctime_s`|`asctime_s`|`_wasctime_s`|  
  
 在 C\+\+ 中，使用这些函数是由重载模板简化；该重载可以自动推断缓冲区长度，而无需指定范围参数。  有关更多信息，请参见[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`asctime_s`|\<time.h\>|  
|`_wasctime_s`|\<time.h\> or \<wchar.h\>|  
  
## 安全性  
 如果缓冲区的指针不是 `NULL`，并且指针不指向有效的缓冲区，函数将覆盖该位置。  这也会导致访问冲突。  
  
 如果传递的大小参数大于缓冲区的实际大小大于，[缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795) 可以发生。  
  
## 示例  
 使用 `asctime_s` 函数，此程序把系统时间存储在长整数 `aclock` 中，将其转换为结构 `newtime` 转换为字符串形式，然后输出。  
  
```  
// crt_asctime_s.c  
#include <time.h>  
#include <stdio.h>  
  
struct tm newtime;  
__time32_t aclock;  
  
int main( void )  
{  
   char buffer[32];  
   errno_t errNum;  
   _time32( &aclock );   // Get time in seconds.  
   _localtime32_s( &newtime, &aclock );   // Convert time to struct tm form.  
  
   // Print local time as a string.  
  
   errNum = asctime_s(buffer, 32, &newtime);  
   if (errNum)  
   {  
       printf("Error code: %d", (int)errNum);  
       return 1;  
   }  
   printf( "Current date and time: %s", buffer );  
   return 0;  
}  
```  
  
  **当前日期和时间：星期三 5 月 14 日 15:30: 17 年 2003**   
## .NET Framework 等效项  
  
-   <xref:System.DateTime.ToLongDateString%2A?displayProperty=fullName>  
  
-   <xref:System.DateTime.ToLongTimeString%2A?displayProperty=fullName>  
  
-   <xref:System.DateTime.ToShortDateString%2A?displayProperty=fullName>  
  
-   <xref:System.DateTime.ToShortTimeString%2A?displayProperty=fullName>  
  
-   <xref:System.DateTime.ToString%2A?displayProperty=fullName>  
  
## 请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [ctime\_s、\_ctime32\_s、\_ctime64\_s、\_wctime\_s、\_wctime32\_s、\_wctime64\_s](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)   
 [\_ftime, \_ftime32, \_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime\_s、\_gmtime32\_s、\_gmtime64\_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime\_s, \_localtime32\_s, \_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [\_tzset](../../c-runtime-library/reference/tzset.md)