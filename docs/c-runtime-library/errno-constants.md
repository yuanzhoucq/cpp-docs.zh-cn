---
title: "errno 常量 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ENOEXEC
- ENOMEM
- E2BIG
- STRUNCATE
- ENOENT
- EMFILE
- EBADF
- EDEADLOCK
- EXDEV
- EILSEQ
- EINVAL
- EDOM
- EACCES
- ERANGE
- ENOSPC
- EAGAIN
- EEXIST
- ECHILD
dev_langs:
- C++
helpviewer_keywords:
- ENOEXEC constant
- EBADF constant
- EAGAIN constant
- EINVAL constant
- ENOENT constant
- errno constants
- E2BIG constant
- EMFILE constant
- EDEADLOCK constant
- ENOSPC constant
- EDOM constant
- ENOMEM constant
- EACCES constant
- EEXIST constant
- STRUNCATE constant
- ERANGE constant
- ECHILD constant
- EXDEV constant
- EILSEQ constant
ms.assetid: 47089258-d5a5-4cd8-b193-223894dea0cf
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 993d61cf94df06c01623f231f3a4915d0ec8cc41
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="errno-constants"></a>errno 常量
## <a name="syntax"></a>语法  
  
```  
  
#include <errno.h>  
```  
  
## <a name="remarks"></a>备注  
 errno 值是在出现各种错误条件时分配给 [errno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 的常量。  
  
 ERRNO.H 包含 errno 值的定义。 但是，并非 ERRNO.H 中给定的提供定义都可用于 32 位 Windows 操作系统。 ERRNO.H 中的某些值的存在是为了保持与 UNIX 系列操作系统的兼容性。  
  
 32 位 Windows 操作系统中的 errno 值是 XENIX 系统中的 errno 值的子集。 因此，errno 值不一定与由从 Windows 操作系统进行的系统调用返回的实际错误代码相同。 若要访问实际操作系统错误代码，请使用包含此值的 _doserrno[](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 变量。  
  
 下列 errno 值受支持：  
  
 **ECHILD**  
 没有生成的进程。  
  
 **EAGAIN**  
 没有其他进程。 尝试创建新进程失败，原因是没有更多的进程槽、没有足够的内存或者已到达最大嵌套级别。  
  
 **E2BIG**  
 自变量列表太长。  
  
 **EACCES**  
 权限被拒绝。 文件的权限设置不允许指定的访问权限。 此错误表示尝试通过与某个文件的特性不兼容的方式访问该文件（或者，在某些情况下为目录）。  
  
 例如，当尝试从未打开的文件读取、打开现有的只读文件进行写入或打开目录而不是文件时，将会发生错误。 在 MS-DOS 操作系统版本 3.0 以及更高版本下，EACCES 也可能表示锁定或共享冲突。  
  
 在尝试重命名文件或目录或者删除现有目录时也可能发生错误。  
  
 **EBADF**  
 文件编号错误。 可能有两种原因：1) 指定的文件描述符不是有效值，或者未引用打开的文件。 2) 尝试写入到已打开进行只读访问的文件或设备。  
  
 **EDEADLOCK**  
 将会发生资源死锁。 数学函数的自变量未在函数域中。  
  
 **EDOM**  
 数学自变量。  
  
 **EEXIST**  
 文件存在。 尝试创建已存在的文件。 例如，在 _open 调用中指定 _O_CREAT 和 _O_EXCL 标志，但命名的文件已存在。  
  
 **EILSEQ**  
 非法字节序列（例如，在 MBCS 字符串中）。  
  
 **EINVAL**  
 无效的参数。 为某个函数的自变量之一给定了无效值。 例如，在定位文件指针时为原始位置给定的值（通过调用 fseek）位于文件头的前面。  
  
 **EMFILE**  
 打开的文件太多。 没有更多文件说明符可用，因此无法打开更多文件。  
  
 **ENOENT**  
 没有此文件或目录。 指定的文件或目录不存在或无法找到。 只要指定的文件不存在或路径的组件未指定现有的目录，就可能出现此消息。  
  
 **ENOEXEC**  
 执行格式错误。 尝试执行不可执行的文件或具有无效的可执行文件格式的文件。  
  
 **ENOMEM**  
 内核不够。 无法为尝试的运算符提供足够的内存。 例如，当可用于执行子进程的内存不足时，或者当无法满足 _getcwd 调用中的分配请求时，就会出现此消息。  
  
 **ENOSPC**  
 设备上没有剩余空间。 设备上没有可供写入的其他空间（例如，当磁盘已满时）。  
  
 **ERANGE**  
 结果太大。 数学函数的自变量太大，造成结果中的有效位部分或全部丢失。 当参数大于预期值时（例如，当 _getcwd 的 buffer 参数大于预期值时），在其他函数中也可能发生此错误。  
  
 **EXDEV**  
 跨设备链接。 尝试将文件移至不同的设备（使用 rename 函数）。  
  
 **STRUNCATE**  
 字符串复制或串联导致字符串被截断。 请参阅 [_TRUNCATE](../c-runtime-library/truncate.md)。  
  
 下列值支持 Posix 的兼容性。 它们都是非 Posix 系统上必需的值。  
  
```  
#define E2BIG [argument list too long]  
#define EACCES [permission denied]  
#define EADDRINUSE [address in use]  
#define EADDRNOTAVAIL [address not available]  
#define EAFNOSUPPORT [address family not supported]  
#define EAGAIN [resource unavailable try again]  
#define EALREADY [connection already in progress]  
#define EBADF [bad file descriptor]  
#define EBADMSG [bad message]  
#define EBUSY [device or resource busy]  
#define ECANCELED [operation canceled]  
#define ECHILD [no child process]  
#define ECONNABORTED [connection aborted]  
#define ECONNREFUSED [connection refused]  
#define ECONNRESET [connection reset]  
#define EDEADLK [resource deadlock would occur]  
#define EDESTADDRREQ [destination address required]  
#define EDOM [argument out of domain]  
#define EEXIST [file exists]  
#define EFAULT [bad address]  
#define EFBIG [file too large]  
#define EHOSTUNREACH [host unreachable]  
#define EIDRM [identifier removed]  
#define EILSEQ [illegal byte sequence]  
#define EINPROGRESS [operation in progress]  
#define EINTR [interrupted]  
#define EINVAL [invalid argument]  
#define EIO [io error]  
#define EISCONN [already connected]  
#define EISDIR [is a directory]  
#define ELOOP [too many synbolic link levels]  
#define EMFILE [too many files open]  
#define EMLINK [too many links]  
#define EMSGSIZE [message size]  
#define ENAMETOOLONG [filename too long]  
#define ENETDOWN [network down]  
#define ENETRESET [network reset]  
#define ENETUNREACH [network unreachable]  
#define ENFILE [too many files open in system]  
#define ENOBUFS [no buffer space]  
#define ENODATA [no message available]  
#define ENODEV [no such device]  
#define ENOENT [no such file or directory]  
#define ENOEXEC [executable format error]  
#define ENOLCK [no lock available]  
#define ENOLINK [no link]  
#define ENOMEM [not enough memory]  
#define ENOMSG [no message]  
#define ENOPROTOOPT [no protocol option]  
#define ENOSPC [no space on device]  
#define ENOSR [no stream resources]  
#define ENOSTR [not a stream]  
#define ENOSYS [function not supported]  
#define ENOTCONN [not connected]  
#define ENOTDIR [not a directory]  
#define ENOTEMPTY [directory not empty]  
#define ENOTRECOVERABLE [state not recoverable]  
#define ENOTSOCK [not a socket]  
#define ENOTSUP [not supported]  
#define ENOTTY [inappropriate io control operation]  
#define ENXIO [no such device or address]  
#define EOPNOTSUPP [operation not supported]  
#define EOTHER [other]  
#define EOVERFLOW [value too large]  
#define EOWNERDEAD [owner dead]  
#define EPERM [operation not permitted]  
#define EPIPE [broken pipe]  
#define EPROTO [protocol error]  
#define EPROTONOSUPPORT [protocol not supported]  
#define EPROTOTYPE [wrong protocol type]  
#define ERANGE [result out of range]  
#define EROFS [read only file system]  
#define ESPIPE [invalid seek]  
#define ESRCH [no such process]  
#define ETIME [stream timeout]  
#define ETIMEDOUT [timed out]  
#define ETXTBSY [text file busy]  
#define EWOULDBLOCK [operation would block]  
#define EXDEV [cross device link]  
```  
  
## <a name="see-also"></a>另请参阅  
 [全局常量](../c-runtime-library/global-constants.md)
