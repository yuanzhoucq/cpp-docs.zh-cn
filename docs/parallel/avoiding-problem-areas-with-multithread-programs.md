---
title: 避免与多线程程序有关的问题
ms.date: 11/04/2016
helpviewer_keywords:
- multithreading [C++], troubleshooting
- errors [C++], multithreaded programs
- threading [C++], troubleshooting
- troubleshooting [C++], multithreading
ms.assetid: 06cc231d-bb5a-409d-8bd3-676c9e2a8c5b
ms.openlocfilehash: 598758a4ceb0a12640faf2832f9f03cd1e44ef9f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461641"
---
# <a name="avoiding-problem-areas-with-multithread-programs"></a>避免与多线程程序有关的问题

有几个创建、 链接，或执行多线程 C 程序中可能会遇到的问题。 一些较为常见的问题是下表中所述。 (从 MFC 的角度的类似讨论，请参阅[多线程处理： 编程提示](multithreading-programming-tips.md)。)

|问题|可能的原因|
|-------------|--------------------|
|获取一个消息框，显示您的程序导致保护冲突。|很多 Win32 编程错误导致保护冲突。 保护冲突的常见原因是间接分配给 null 指针的数据。 因为这会导致程序试图访问不属于它的内存，则会发出保护冲突。<br /><br /> 轻松地检测保护违规的原因是编译您的程序与调试信息并运行通过 Visual c + + 环境中的调试器。 保护错误发生时，Windows 将控制转移到调试器，并将光标置于引起问题的行。|
|您的程序会生成大量的编译和链接错误。|可以通过编译器的警告级别设置为其最大的值之一，并注意警告消息来消除许多潜在的问题。 通过使用级别 3 或 4 级警告级别选项，则可以检测到意外的数据转换、 缺少函数原型，并使用非 ANSI 功能。|

## <a name="see-also"></a>请参阅

[使用 C 和 Win32 进行多线程编程](multithreading-with-c-and-win32.md)