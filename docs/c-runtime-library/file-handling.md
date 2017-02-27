---
title: "文件处理 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.files
dev_langs:
- C++
helpviewer_keywords:
- files [C++], handling
- files [C++], opening
- files [C++], manipulating
ms.assetid: 48119e2e-e94f-4602-b08b-b72440f731d8
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 28ee6adcd86814d5804e0d9d34dd27a3c6d22f71

---
# <a name="file-handling"></a>文件处理
使用这些例程可创建、删除和操作文件以及设置和检查文件访问权限。  
  
 C 运行时库将任何时候可以打开的文件数限制为 512。 试图打开超过最大数量的文件描述符或文件流会导致程序失败。 使用 [_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md) 更改此数量。  
  
 以下例程对文件描述符指定的文件进行操作。  
  
### <a name="file-handling-routines-file-descriptor"></a>文件处理例程（文件描述符）  
  
|例程|使用|.NET Framework 等效项|  
|-------------|---------|-------------------------------|  
|[_chsize](../c-runtime-library/reference/chsize.md)、[_chsize_s](../c-runtime-library/reference/chsize-s.md)|更改文件大小|[System::IO::Stream::SetLength](https://msdn.microsoft.com/en-us/library/system.io.stream.setlength.aspx)、 [System::IO::FileStream::SetLength](https://msdn.microsoft.com/en-us/library/system.io.filestream.setlength.aspx)|  
|[_filelength、_filelengthi64](../c-runtime-library/reference/filelength-filelengthi64.md)|获取文件长度|[System::IO::Stream::Length](https://msdn.microsoft.com/en-us/library/system.io.stream.length.aspx)、 [System::IO::FileStream::Length](https://msdn.microsoft.com/en-us/library/system.io.filestream.length.aspx)|  
|[_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)|获取有关描述符的文件状态信息|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_get_osfhandle](../c-runtime-library/reference/get-osfhandle.md)|返回与现有 C 运行时文件描述符关联的操作系统文件句柄|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_isatty](../c-runtime-library/reference/isatty.md)|检查字符设备|[System::IO::Stream::CanWrite](https://msdn.microsoft.com/en-us/library/system.io.filestream.canwrite.aspx)、 [System::IO::FileStream::CanWrite](https://msdn.microsoft.com/en-us/library/system.io.stream.canwrite.aspx)|  
|[_locking](../c-runtime-library/reference/locking.md)|锁定文件的区域|[System::IO::FileStream::Lock](https://msdn.microsoft.com/en-us/library/system.io.filestream.lock.aspx)|  
|[_open_osfhandle](../c-runtime-library/reference/open-osfhandle.md)|将 C 运行时文件描述符与现有操作系统文件句柄关联|[System::IO::FileStream::Handle](https://msdn.microsoft.com/en-us/library/system.io.filestream.handle.aspx)|  
|[_setmode](../c-runtime-library/reference/setmode.md)|设置文件转换模式|[System::IO::BinaryReader 类](https://msdn.microsoft.com/en-us/library/system.io.binaryreader.aspx)、 [System::IO::TextReader 类](https://msdn.microsoft.com/en-us/library/system.io.textreader.aspx)|  
  
 以下例程对路径或文件名指定的文件进行操作。  
  
### <a name="file-handling-routines-path-or-filename"></a>文件处理例程（路径或文件名）  
  
|例程|使用|.NET Framework 等效项|  
|-------------|---------|-------------------------------|  
|[_access、_waccess](../c-runtime-library/reference/access-waccess.md)、[_access_s、_waccess_s](../c-runtime-library/reference/access-s-waccess-s.md)|检查文件权限设置|[System::IO::FileAccess 枚举](https://msdn.microsoft.com/en-us/library/4z36sx0f.aspx)|  
|[_chmod、_wchmod](../c-runtime-library/reference/chmod-wchmod.md)|更改文件权限设置|[System::IO::File::SetAttributes](https://msdn.microsoft.com/en-us/library/system.io.file.setattributes.aspx)、 [System::Security::Permissions::FileIOPermission](https://msdn.microsoft.com/en-us/library/system.security.permissions.fileiopermission.aspx)|  
|[_fullpath、_wfullpath](../c-runtime-library/reference/fullpath-wfullpath.md)|将相对路径扩展为其绝对路径名|[System::IO::File::Create](https://msdn.microsoft.com/en-us/library/system.io.file.create.aspx)|  
|[_makepath、_wmakepath](../c-runtime-library/reference/makepath-wmakepath.md)、[_makepath_s、_wmakepath_s](../c-runtime-library/reference/makepath-s-wmakepath-s.md)|将路径组件合并为单个完整路径|[System::IO::File::Create](https://msdn.microsoft.com/en-us/library/system.io.file.create.aspx)|  
|[_mktemp、_wmktemp](../c-runtime-library/reference/mktemp-wmktemp.md)、[_mktemp_s、_wmktemp_s](../c-runtime-library/reference/mktemp-s-wmktemp-s.md)|创建唯一的文件名|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[remove、_wremove](../c-runtime-library/reference/remove-wremove.md)|删除文件|[System::IO::File::Delete](https://msdn.microsoft.com/en-us/library/system.io.file.delete.aspx)|  
|[rename、_wrename](../c-runtime-library/reference/rename-wrename.md)|重命名文件|[System::IO::File::Move](https://msdn.microsoft.com/en-us/library/system.io.file.move.aspx)|  
|[_splitpath、_wsplitpath](../c-runtime-library/reference/splitpath-wsplitpath.md)、[_splitpath_s、_wsplitpath_s](../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)|将路径分析为组件|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_stat、_stat64、_stati64、_wstat、_wstat64、_wstati64](../c-runtime-library/reference/stat-functions.md)|获取有关命名文件的文件状态信息|[System::IO::File::GetAttributes](https://msdn.microsoft.com/en-us/library/system.io.file.getattributes.aspx)、 [System::IO::File::GetCreationTime](https://msdn.microsoft.com/en-us/library/system.io.file.getcreationtime.aspx)、 [System::IO::File::GetLastAccessTime](https://msdn.microsoft.com/en-us/library/system.io.file.getlastaccesstime.aspx)、 [System::IO::File::GetLastWriteTime](https://msdn.microsoft.com/en-us/library/system.io.file.getlastwritetime.aspx)|  
|[_umask](../c-runtime-library/reference/umask.md)、[_umask_s](../c-runtime-library/reference/umask-s.md)|为程序创建的新文件设置默认权限掩码|[System::IO::File::SetAttributes](https://msdn.microsoft.com/en-us/library/system.io.file.setattributes.aspx)|  
|[_unlink、_wunlink](../c-runtime-library/reference/unlink-wunlink.md)|删除文件|[System::IO::File::Delete](https://msdn.microsoft.com/en-us/library/system.io.file.delete.aspx)|  
  
 以下例程打开文件。  
  
### <a name="file-handling-routines-open-file"></a>文件处理例程（打开文件）  
  
|例程|使用|.NET Framework 等效项|  
|-------------|---------|-------------------------------|  
|[fopen、_wfopen](../c-runtime-library/reference/fopen-wfopen.md)、[fopen_s、_wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)|打开文件并返回指向打开的文件的指针。|[System::IO::File::Open](https://msdn.microsoft.com/en-us/library/system.io.file.open.aspx)、<xref:System.IO.FileStream.%23ctor%2A>|  
|[_fsopen、_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)|打开具有文件共享的流并返回指向打开的文件的指针。|[System::IO::File::Open](https://msdn.microsoft.com/en-us/library/system.io.file.open.aspx)、<xref:System.IO.FileStream.%23ctor%2A>|  
|[_open、_wopen](../c-runtime-library/reference/open-wopen.md)|打开文件并返回打开的文件的文件描述符。|[System::IO::File::Open](https://msdn.microsoft.com/en-us/library/system.io.file.open.aspx)、<xref:System.IO.FileStream.%23ctor%2A>|  
|[_sopen、_wsopen](../c-runtime-library/reference/sopen-wsopen.md)、[_sopen_s、_wsopen_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)|打开具有文件共享的文件并返回打开的文件的文件描述符。||  
|[_pipe](../c-runtime-library/reference/pipe.md)|创建用于读取和写入的管道。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[freopen、_wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)、[freopen_s、_wfreopen_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|重新分配文件指针。|[System::IO::File::Open](https://msdn.microsoft.com/en-us/library/system.io.file.open.aspx)、<xref:System.IO.FileStream.%23ctor%2A>|  
  
 以下函数提供一种方法，用于在 `FILE` 结构、文件描述符与 Win32 文件句柄之间更改文件的表示形式。  
  
||||  
|-|-|-|  
|[_fdopen、_wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)|将流与以前为低级别 I/O 而打开的文件相关联，并返回指向打开的流的指针。|[System::IO::File::Open](https://msdn.microsoft.com/en-us/library/system.io.filestream.aspx)|  
|[_fileno](../c-runtime-library/reference/fileno.md)|获取与流关联的文件描述符。|[System::IO::FileStream::Handle](https://msdn.microsoft.com/en-us/library/system.io.filestream.handle.aspx)|  
|[_get_osfhandle](../c-runtime-library/reference/get-osfhandle.md)|返回与现有 C 运行时文件描述符关联的操作系统文件句柄|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_open_osfhandle](../c-runtime-library/reference/open-osfhandle.md)|将 C 运行时文件描述符与现有操作系统文件句柄关联。|[System::IO::FileStream::Handle](https://msdn.microsoft.com/en-us/library/system.io.filestream.handle.aspx)|  
  
 以下 Win32 函数也打开文件和管道：  
  
-   [CreateFile](http://msdn.microsoft.com/library/windows/desktop/aa363858.aspx)  
  
-   [CreatePipe](http://msdn.microsoft.com/library/windows/desktop/aa365152.aspx)  
  
-   [CreateNamedPipe](http://msdn.microsoft.com/library/windows/desktop/aa365150.aspx)  
  
## <a name="see-also"></a>另请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)   
 [目录控制](../c-runtime-library/directory-control.md)   
 [系统调用](../c-runtime-library/system-calls.md)


<!--HONumber=Feb17_HO4-->


