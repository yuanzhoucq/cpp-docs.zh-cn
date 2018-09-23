---
title: 低级别 I/O | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.io
dev_langs:
- C++
helpviewer_keywords:
- I/O [CRT], low-level
- I/O [CRT], functions
- low-level I/O routines
- file handles [C++]
- file handles [C++], I/O functions
ms.assetid: 53e11bdd-6720-481c-8b2b-3a3a569ed534
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d263d1d61a6dcc6921d6918db2b89386e918551
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018309"
---
# <a name="low-level-io"></a>低级别 I/O

这些函数将为低于流 I/O 提供的操作的低级别操作直接调用操作系统。 低级别输入和输出调用不会缓冲数据或设置数据格式。

低级别例程可以使用以下预定义的文件描述符访问程序启动时打开的标准流。

|流|文件描述符|
|------------|---------------------|
|**stdin**|0|
|**stdout**|1|
|**stderr**|2|

发生错误时，低级别 I/O 例程将设置 [errno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 全局变量。 只有在程序需要 STDIO.H 中定义的常量（例如文件尾指示符 (EOF)）时，在使用低级别函数时必须将 STDIO.H 包含在内。

## <a name="low-level-io-functions"></a>低级别 I/O 函数

|函数|使用|
|--------------|---------|
|[_close](../c-runtime-library/reference/close.md)|关闭文件|
|[_commit](../c-runtime-library/reference/commit.md)|将文件刷新到磁盘|
|[_creat、_wcreat](../c-runtime-library/reference/creat-wcreat.md)|创建文件|
|[_dup](../c-runtime-library/reference/dup-dup2.md)|返回给定文件的下一个可用文件描述符|
|[_dup2](../c-runtime-library/reference/dup-dup2.md)|为给定文件创建第二个描述符|
|[_eof](../c-runtime-library/reference/eof.md)|测试文件尾|
|[_lseek、_lseeki64](../c-runtime-library/reference/lseek-lseeki64.md)|将文件指针重新定位到给定位置|
|[_open、_wopen](../c-runtime-library/reference/open-wopen.md)|打开文件|
|[_read](../c-runtime-library/reference/read.md)|读取文件中的数据|
|[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md), [_sopen_s, _wsopen_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)|打开用于文件共享的文件|
|[_tell、_telli64](../c-runtime-library/reference/tell-telli64.md)|获取当前文件指针位置|
|[_umask](../c-runtime-library/reference/umask.md), [_umask_s](../c-runtime-library/reference/umask-s.md)|设置文件权限掩码|
|[_write](../c-runtime-library/reference/write.md)|将数据写入文件|

 _dup 和 _dup2 通常用于将预定义文件描述符与其他文件关联。

## <a name="see-also"></a>请参阅

[输入和输出](../c-runtime-library/input-and-output.md)<br/>
[按类别分的通用 C 运行时例程](../c-runtime-library/run-time-routines-by-category.md)<br/>
[系统调用](../c-runtime-library/system-calls.md)<br/>
