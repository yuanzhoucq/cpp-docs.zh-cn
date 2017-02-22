---
title: "errno 常量 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ENOEXEC"
  - "ENOMEM"
  - "E2BIG"
  - "STRUNCATE"
  - "ENOENT"
  - "EMFILE"
  - "EBADF"
  - "EDEADLOCK"
  - "EXDEV"
  - "EILSEQ"
  - "EINVAL"
  - "EDOM"
  - "EACCES"
  - "ERANGE"
  - "ENOSPC"
  - "EAGAIN"
  - "EEXIST"
  - "ECHILD"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "E2BIG 常量"
  - "EACCES 常量"
  - "EAGAIN 常量"
  - "EBADF 常量"
  - "ECHILD 常量"
  - "EDEADLOCK 常量"
  - "EDOM 常量"
  - "EEXIST 常量"
  - "EILSEQ 常量"
  - "EINVAL 常量"
  - "EMFILE 常量"
  - "ENOENT 常量"
  - "ENOEXEC 常量"
  - "ENOMEM 常量"
  - "ENOSPC 常量"
  - "ERANGE 常量"
  - "errno 常量"
  - "EXDEV 常量"
  - "STRUNCATE 常量"
ms.assetid: 47089258-d5a5-4cd8-b193-223894dea0cf
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# errno 常量
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
#include <errno.h>  
```  
  
## 备注  
 **errno** 值是在各状态错误情况下为 [errno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 分配的常数。  
  
 ERRNO.H 包含 **errno** 值的定义。  但是，并非所有在 ERRNO.H 的定义都可以在 32 位 Windows 操作系统上使用。  某些 ERRNO.H 中的值仍保持与 UNIX 系列操作系统的兼容性。  
  
 在 32 位 Windows 操作系统的 **errno** 值是XENIX 系统中 **errno**值的子集。  因此，**errno** 值不一定与从 Windows 操作系统调用返回的实际错误代码相同。  若要访问实际操作系统错误代码，请使用 [\_doserrno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 变量，此变量包含该值。  
  
 下列**errno** 值是受支持的：  
  
 **ECHILD**  
 未指定的进程。  
  
 **EAGAIN**  
 没有其他进程。  尝试创建新进程失败，因为没有更多的进程槽，或者没有足够的内存，或已到达最大嵌套级。  
  
 **E2BIG**  
 参数列表太长。  
  
 **EACCES**  
 权限被拒绝。  文件权限的设置不允许指定的访问权限。  此错误指示尝试用不兼容的文件属性的方法访问一个文件 \(或，在某些情况下，是目录\)。  
  
 例如，当尝试从未打开的文件读取，编写只读文件，或者打开目录而不是文件时，发生该错误。  在 MS\-DOS 操作系统版本 3.0 和以后的版本，**EACCES** 也可能表示存在阻塞或共享冲突。  
  
 尝试重命名文件或目录重命名来移除现有的目录时也将发生错误。  
  
 **EBADF**  
 错误文件号。  有两种可能原因：1\) 被指定的文件描述符不是有效值或不涉及打开文件。2\) 尝试对只读文件或访问设备进行写入操作。  
  
 **死锁**  
 会发生资源死锁。  算术函数的参数不在函数域中。  
  
 **EDOM**  
 算术参数。  
  
 **EEXIST**  
 文件存在。  尝试创建已存在的文件。  例如，在 **\_open**调用中，指定**\_O\_CREAT** 和 **\_O\_EXCL**标志，但命名文件已存在。  
  
 **EILSEQ**  
 非法字节序列 \(例如，MBCS 字符串\)。  
  
 **EINVAL**  
 参数无效。  给定函数某个参数的无效值。  例如，在文件的开头之前确定文件指针时，给定原点值 \(通过对 **fseek**的调用\)。  
  
 **EMFILE**  
 许多开启文件。  没有其他文件说明符是可用的，因此，无法打开其他文件。  
  
 **ENOENT**  
 不存在这样的文件或目录。  指定的文件或目录不存在或无法找到。  只要已指定的文件不存在或路径中的组件不指定现有的目录，都发生此消息。  
  
 **ENOEXEC**  
 可执行格式错误。  尝试执行一个不可执行的文件或有一个无效的文件格式的文件。  
  
 **ENOMEM**  
 不够核心。  没有足够的内存用于尝试的运算符。  例如，当执行子进程的内存不足时，或者，当**\_getcwd** 调用的分配请求未得到满足时，此消息会出现。  
  
 **ENOSPC**  
 设备上未留下任何空间。  在设备上，没有其他空间用于编写 \(例如，磁盘已满时\)。  
  
 **ERANGE**  
 结果太大。  算术函数的参数太大，导致结果发生部分或全部有效位丢失。  当参数比预期值大得多时 \(例如，当**\_getcwd**的*缓冲区* 的参数比预期长时\)，此错误也会在其他函数出现。  
  
 **EXDEV**  
 跨设备链接。  尝试将文件移至不同的设备 \(使用 **rename** 函数\)。  
  
 **STRUNCATE**  
 字符串复制或串联导致字符串截断。  请参见[\_TRUNCATE](../c-runtime-library/truncate.md)。  
  
 下列值支持 Posix 的兼容性。  它们非 Posix 系统上的需要值。  
  
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
  
## 请参阅  
 [全局常量](../c-runtime-library/global-constants.md)