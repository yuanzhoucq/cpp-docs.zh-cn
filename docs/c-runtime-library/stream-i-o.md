---
title: 流 I/O
ms.date: 11/04/2016
helpviewer_keywords:
- I/O routines, stream I/O
- I/O [CRT], stream
- stream I/O
ms.assetid: dc7874d3-a91b-456a-9015-4748bb358217
ms.openlocfilehash: 0fc49d4cd26593cb02a2ff05c3205cc630ef848c
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444616"
---
# <a name="stream-io"></a>流 I/O

这些函数处理不同大小和格式的数据，从单个字符到大型数据结构都有。 它们还提供缓冲区，这样能提高性能。 流缓冲区的默认大小为 4K。 这些例程会仅影响由运行时库例程创建的缓冲区，对由操作系统创建的缓冲区不起作用。

## <a name="stream-io-routines"></a>流 I/O 例程

|例程|使用|
|-------------|---------|
|[clearerr](../c-runtime-library/reference/clearerr.md)、 [clearerr_s](../c-runtime-library/reference/clearerr-s.md)|清除流的错误指示器|
|[fclose](../c-runtime-library/reference/fclose-fcloseall.md)|关闭流|
|[_fcloseall](../c-runtime-library/reference/fclose-fcloseall.md)|关闭除 stdin、stdout 和 stderr 之外的所有流|
|[_fdopen、wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)|将流与打开的文件的文件描述符相关联|
|[feof](../c-runtime-library/reference/feof.md)|在流上测试文件尾|
|[ferror](../c-runtime-library/reference/ferror.md)|在流上测试错误|
|[fflush](../c-runtime-library/reference/fflush.md)|刷新到缓冲区或存储设备的流|
|[fgetc、fgetwc](../c-runtime-library/reference/fgetc-fgetwc.md)|从流（getc 和 getwc 的函数版本）读取字符|
|[_fgetchar、_fgetwchar](../c-runtime-library/reference/fgetc-fgetwc.md)|从 stdin（getchar 和 getwchar 的函数版本）读取字符|
|[fgetpos](../c-runtime-library/reference/fgetpos.md)|获取流的位置指示器|
|[fgets、fgetws](../c-runtime-library/reference/fgets-fgetws.md)|从流读取字符串|
|[_fileno](../c-runtime-library/reference/fileno.md)|获取与流关联的文件描述符|
|[_flushall](../c-runtime-library/reference/flushall.md)|刷新所有到缓冲区或存储设备的流|
|[fopen、_wfopen](../c-runtime-library/reference/fopen-wfopen.md)、 [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)|打开流|
|[fprintf、_fprintf_l、fwprintf、_fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)、[fprintf_s、_fprintf_s_l、fwprintf_s、_fwprintf_s_l](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|将格式化数据写入流|
|[fputc、fputwc](../c-runtime-library/reference/fputc-fputwc.md)|将字符写入流（putc 和 putwc 的函数版本）|
|[_fputchar、_fputwchar](../c-runtime-library/reference/fputc-fputwc.md)|将字符写入 stdout（putchar 和 putwchar 的函数版本）|
|[fputs、fputws](../c-runtime-library/reference/fputs-fputws.md)|将字符串写入流|
|[fread](../c-runtime-library/reference/fread.md)|从流中读取未格式化的数据|
|[freopen、_wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)、 [freopen_s, _wfreopen_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|重新将 FILE 流指针分配到新的文件或设备|
|[fscanf、fwscanf](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)、[fscanf_s、_fscanf_s_l、fwscanf_s、_fwscanf_s_l](../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)|从流中读取格式化数据|
|[fseek、_fseeki64](../c-runtime-library/reference/fseek-fseeki64.md)|将文件位置移动到给定位置|
|[fsetpos](../c-runtime-library/reference/fsetpos.md)|设置流的位置指示器|
|[_fsopen、_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)|打开具有文件共享的流|
|[ftell、_ftelli64](../c-runtime-library/reference/ftell-ftelli64.md)|获取当前文件位置|
|[fwrite](../c-runtime-library/reference/fwrite.md)|将未格式化的数据项目写入流|
|[getc、getwc](../c-runtime-library/reference/getc-getwc.md)|从流（fgetc 和 fgetwc 的宏版本）读取字符|
|[getchar、getwchar](../c-runtime-library/reference/getc-getwc.md)|从 stdin（fgetchar 和 fgetwchar 的宏版本）读取字符|
|[_getmaxstdio](../c-runtime-library/reference/getmaxstdio.md)|返回在 I/O 流级别允许同时打开的文件数。|
|[gets_s、_getws_s](../c-runtime-library/reference/gets-s-getws-s.md)|从 stdin 读取行|
|[_getw](../c-runtime-library/reference/getw.md)|从流读取二进制 int|
|[printf、_printf_l、wprintf、_wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)、[printf_s、_printf_s_l、wprintf_s、_wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|将格式化数据写入 stdout|
|[putc、putwc](../c-runtime-library/reference/putc-putwc.md)|将字符写入流（fputc 和 fputwc 的宏版本）|
|[putchar、putwchar](../c-runtime-library/reference/putc-putwc.md)|将字符写入 stdout（fputchar 和 fputwchar 的宏版本）|
|[puts、_putws](../c-runtime-library/reference/puts-putws.md)|将行写入流|
|[_putw](../c-runtime-library/reference/putw.md)|将二进制 int 写入流|
|[rewind](../c-runtime-library/reference/rewind.md)|将文件位置移动到的流的开头|
|[_rmtmp](../c-runtime-library/reference/rmtmp.md)|删除由 tmpfile 创建的临时文件|
|[scanf、_scanf_l、wscanf、_wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)、[scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)|从 stdin 读取格式化数据|
|[setbuf](../c-runtime-library/reference/setbuf.md)|控制流缓冲|
|[_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md)|设置在流 I/O 级别同时打开的最大文件数。|
|[setvbuf](../c-runtime-library/reference/setvbuf.md)|控制流缓冲和缓冲区大小|
|[_snprintf、_snwprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)、 [_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l](../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)|将指定长度的格式化数据写入字符串|
|[_snscanf、_snwscanf](../c-runtime-library/reference/snscanf-snscanf-l-snwscanf-snwscanf-l.md)、[_snscanf_s、_snscanf_s_l、_snwscanf_s、_snwscanf_s_l](../c-runtime-library/reference/snscanf-s-snscanf-s-l-snwscanf-s-snwscanf-s-l.md)|从标准输入流读取指定长度的格式化数据。|
|[sprintf、swprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)、[sprintf_s、_sprintf_s_l、swprintf_s、_swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|将格式化数据写入字符串|
|[sscanf、swscanf](../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)、[sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l](../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)|从字符串读取格式化数据|
|[_tempnam、_wtempnam](../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|在给定目录中生成临时文件名|
|[tmpfile](../c-runtime-library/reference/tmpfile.md)、 [tmpfile_s](../c-runtime-library/reference/tmpfile-s.md)|创建临时文件|
|[tmpnam、_wtmpnam](../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)、 [tmpnam_s, _wtmpnam_s](../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md)|生成临时文件名|
|[ungetc、ungetwc](../c-runtime-library/reference/ungetc-ungetwc.md)|将字符推送回流上|
|[_vcprintf、_vcwprintf](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md)、[_vcprintf_s、_vcprintf_s_l、_vcwprintf_s、_vcwprintf_s_l](../c-runtime-library/reference/vcprintf-s-vcprintf-s-l-vcwprintf-s-vcwprintf-s-l.md)|将格式化数据写入控制台。|
|[vfprintf、vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)、[vfprintf_s、_vfprintf_s_l、vfwprintf_s、_vfwprintf_s_l](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|将格式化数据写入流|
|[vprintf、vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)、[vprintf_s、_vprintf_s_l、vwprintf_s、_vwprintf_s_l](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|将格式化数据写入 stdout|
|[_vsnprintf、_vsnwprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md)、[vsnprintf_s、_vsnprintf_s、_vsnprintf_s_l、_vsnwprintf_s、_vsnwprintf_s_l](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)|将指定长度的格式化数据写入缓冲区|
|[vsprintf、vswprintf](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)、[vsprintf_s、_vsprintf_s_l、vswprintf_s、_vswprintf_s_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|将格式化数据写入缓冲区|

当程序开始执行时，启动代码将自动开启若干流：标准输入（由 stdin 指向）、标准输出（由 stdout 指向）和标准错误（由 stderr 指向）。 默认情况下，这些流将定向到控制台（键盘和屏幕）。 使用 freopen，将 stdin、stdout 或 stderr 重定向到磁盘文件或设备。

默认情况下，会对使用流例程打开的文件执行缓冲操作。 当 stdout 和 stderr 函数是完整的，或在进行了每次库调用之后要写入字符设备，则这将刷新两个函数。 如果某个程序异常终止，则可能不会刷新输出缓冲区，从而导致数据丢失。 使用 fflush 或 _flushall 以确保与指定文件相关联的缓冲区或所有打开的缓冲区被刷新到操作系统，操作系统在将数据写入磁盘之前可缓存数据。 “提交到磁盘”功能可确保刷新的缓冲区内容不会在出现系统故障时丢失。

有两种方法将缓冲区内容提交到磁盘：

- 与文件 COMMODE.OBJ 链接以设置全局提交标志。 全局标志的默认设置是 n，意味着“不提交”。

- 使用 fopen 或 _fdopen 将模式标志设置为 c。

专门使用 c 或 n 标志打开的任何文件的行为以该标志为准，而不考虑全局提交/不提交标志的状态。

如果你的程序未显式关闭流，则程序终止时流会自动关闭。 但是，你应在程序完成流操作时关闭流，因为可以同时打开的流的数量是有限。 请参阅 [_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md) 获取有关此限制的信息。

只有通过对 fflush 或对文件定位函数（fseek、fsetpos 或 rewind）进行干预调用时，输入才能直接跟随输出。 如果输入操作遇到文件末尾，则输出可以在没有对文件定位函数进行干预调用的情况下跟随输入。

## <a name="see-also"></a>另请参阅

[输入和输出](../c-runtime-library/input-and-output.md)<br/>
[按类别分的通用 C 运行时例程](../c-runtime-library/run-time-routines-by-category.md)<br/>
