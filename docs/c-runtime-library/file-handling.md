---
title: "文件处理 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.files
dev_langs: C++
helpviewer_keywords:
- files [C++], handling
- files [C++], opening
- files [C++], manipulating
ms.assetid: 48119e2e-e94f-4602-b08b-b72440f731d8
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 129267c69a2cf4830587f8ebc7c445a01591235b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="file-handling"></a>文件处理
使用这些例程可创建、删除和操作文件以及设置和检查文件访问权限。  
  
 C 运行时库将任何时候可以打开的文件数限制为 512。 试图打开超过最大数量的文件描述符或文件流会导致程序失败。 使用 [_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md) 可更改此数量。  
  
### <a name="file-handling-routines-file-descriptor"></a>文件处理例程（文件描述符）  
  
 这些例程对文件描述符指定的文件进行操作。  
  
|例程所返回的值|使用|  
|-------------|---------|  
|[_chsize](../c-runtime-library/reference/chsize.md)，[_chsize_s](../c-runtime-library/reference/chsize-s.md)|更改文件大小|  
|[_filelength、_filelengthi64](../c-runtime-library/reference/filelength-filelengthi64.md)|获取文件长度|  
|[_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)|获取有关描述符的文件状态信息|  
|[_get_osfhandle](../c-runtime-library/reference/get-osfhandle.md)|返回与现有 C 运行时文件描述符关联的操作系统文件句柄|  
|[_isatty](../c-runtime-library/reference/isatty.md)|检查字符设备|  
|[_locking](../c-runtime-library/reference/locking.md)|锁定文件的区域|  
|[_open_osfhandle](../c-runtime-library/reference/open-osfhandle.md)|将 C 运行时文件描述符与现有操作系统文件句柄关联|  
|[_setmode](../c-runtime-library/reference/setmode.md)|设置文件转换模式|  
  
### <a name="file-handling-routines-path-or-filename"></a>文件处理例程（路径或文件名）  
  
 这些例程对路径或文件名指定的文件进行操作。  
  
|例程所返回的值|使用|  
|-------------|---------|  
|[_access, _waccess](../c-runtime-library/reference/access-waccess.md), [_access_s, _waccess_s](../c-runtime-library/reference/access-s-waccess-s.md)|检查文件权限设置|  
|[_chmod、_wchmod](../c-runtime-library/reference/chmod-wchmod.md)|更改文件权限设置|  
|[_fullpath、_wfullpath](../c-runtime-library/reference/fullpath-wfullpath.md)|将相对路径扩展为其绝对路径名|  
|[_makepath, _wmakepath](../c-runtime-library/reference/makepath-wmakepath.md), [_makepath_s, _wmakepath_s](../c-runtime-library/reference/makepath-s-wmakepath-s.md)|将路径组件合并为单个完整路径|  
|[_mktemp、_wmktemp](../c-runtime-library/reference/mktemp-wmktemp.md)、 [_mktemp_s, _wmktemp_s](../c-runtime-library/reference/mktemp-s-wmktemp-s.md)|创建唯一的文件名|  
|[remove、_wremove](../c-runtime-library/reference/remove-wremove.md)|删除文件|  
|[rename、_wrename](../c-runtime-library/reference/rename-wrename.md)|重命名文件|  
|[_splitpath、_wsplitpath](../c-runtime-library/reference/splitpath-wsplitpath.md)、 [_splitpath_s, _wsplitpath_s](../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)|将路径分析为组件|  
|[_stat、_stat64、_stati64、_wstat、_wstat64、_wstati64](../c-runtime-library/reference/stat-functions.md)|获取有关命名文件的文件状态信息|  
|[_umask](../c-runtime-library/reference/umask.md), [_umask_s](../c-runtime-library/reference/umask-s.md)|为程序创建的新文件设置默认权限掩码|  
|[_unlink、_wunlink](../c-runtime-library/reference/unlink-wunlink.md)|删除文件|  
  
### <a name="file-handling-routines-open-file"></a>文件处理例程（打开文件）  
  
 这些例程打开文件。  
  
|例程所返回的值|使用|  
|-------------|---------|  
|[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md), [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)|打开文件并返回指向打开的文件的指针。|  
|[_fsopen、_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)|打开具有文件共享的流并返回指向打开的文件的指针。|  
|[_open、_wopen](../c-runtime-library/reference/open-wopen.md)|打开文件并返回打开的文件的文件描述符。|  
|[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md), [_sopen_s, _wsopen_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)|打开具有文件共享的文件并返回打开的文件的文件描述符。|  
|[_pipe](../c-runtime-library/reference/pipe.md)|创建用于读取和写入的管道。|  
|[freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md), [freopen_s, _wfreopen_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|重新分配文件指针。|  
  
 这些例程提供一种方法，用于在 `FILE` 结构、文件描述符与 Win32 文件句柄之间更改文件的表示形式。  
  
|例程所返回的值|使用|  
|-------------|---------|  
|[_fdopen、_wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)|将流与以前为低级别 I/O 而打开的文件相关联，并返回指向打开的流的指针。|  
|[_fileno](../c-runtime-library/reference/fileno.md)|获取与流关联的文件描述符。|  
|[_get_osfhandle](../c-runtime-library/reference/get-osfhandle.md)|返回与现有 C 运行时文件描述符关联的操作系统文件句柄|  
|[_open_osfhandle](../c-runtime-library/reference/open-osfhandle.md)|将 C 运行时文件描述符与现有操作系统文件句柄关联。|  
  
 以下 Win32 函数也打开文件和管道：  
  
-   [CreateFile](http://msdn.microsoft.com/library/windows/desktop/aa363858.aspx)  
  
-   [CreatePipe](http://msdn.microsoft.com/library/windows/desktop/aa365152.aspx)  
  
-   [CreateNamedPipe](http://msdn.microsoft.com/library/windows/desktop/aa365150.aspx)  
  
## <a name="see-also"></a>请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)   
 [目录控制](../c-runtime-library/directory-control.md)   
 [系统调用](../c-runtime-library/system-calls.md)