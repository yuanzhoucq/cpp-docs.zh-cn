---
title: C 运行时错误 R6016
ms.date: 11/04/2016
f1_keywords:
- R6016
helpviewer_keywords:
- R6016
ms.assetid: 7bd3f274-d9c4-4bc4-8252-80bf168c4c3a
ms.openlocfilehash: 22bf4b7e8951215d1a013edb29af1ebff7517ffc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197335"
---
# <a name="c-runtime-error-r6016"></a>C 运行时错误 R6016

线程数据所需的空间不足

> [!NOTE]
> 如果在运行应用程序时遇到此错误消息，则该应用程序已关闭，因为它具有内部内存问题。 导致此错误的可能原因有很多，但通常是由于内存不足情况、应用程序中的 bug 或应用程序使用的外接程序或扩展中的 bug 引起的。
>
> 可以尝试以下步骤来修复此错误：
>
> - 关闭其他正在运行的应用程序或重新启动计算机以释放内存。
> - 使用**控制面板**中的 "**应用和功能**" 或 "**程序和功能**" 页来修复或重新安装应用。
> - 使用**控制面板**中的 "**应用和功能**" 或 "**程序和功能**" 页，可以删除、修复或重新安装应用程序使用的外接程序或扩展。
> - 检查 "**控制面板**" 中的 "软件更新" **Windows 更新**。
> - 检查应用的更新版本。 如果问题仍然存在，请与应用程序供应商联系。

**面向程序员的信息**

之所以发生此错误，是因为程序没有从操作系统收到足够的内存来完成[_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md)或 `_beginthreadex` 调用，或者线程本地存储尚未 `_beginthread` 或 `_beginthreadex`初始化。

新线程启动时，库必须为该线程创建一个内部数据库。 如果数据库无法通过使用操作系统提供的内存进行扩展，则该线程不会开始并且此调用进程会停止。 当此进程创建了过多线程或线程本地存储用完时，就会发生这种情况。

建议调用 C 运行时库（CRT）的可执行文件应使用 `_beginthreadex` 来创建线程而不是 Windows API `CreateThread`。 `_beginthreadex` 将在线程本地存储中初始化很多 CRT 函数使用的内部静态存储。 如果使用 `CreateThread` 创建线程，则在调用需要初始化的内部静态存储的 CRT 函数时，CRT 可能会使用 R6016 终止此进程。
