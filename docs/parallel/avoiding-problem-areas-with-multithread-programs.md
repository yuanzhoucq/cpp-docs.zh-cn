---
title: "避免与多线程程序问题 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- multithreading [C++], troubleshooting
- errors [C++], multithreaded programs
- threading [C++], troubleshooting
- troubleshooting [C++], multithreading
ms.assetid: 06cc231d-bb5a-409d-8bd3-676c9e2a8c5b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9a6722e2cea4141a44bee43a162a73176ce35fea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="avoiding-problem-areas-with-multithread-programs"></a>避免与多线程程序有关的问题
有几个问题可能会创建、 链接或执行多线程 C 程序中出现。 下表介绍了一些较为常见的问题。 (从 MFC 角度来看的类似讨论，请参阅[多线程处理： 编程提示](../parallel/multithreading-programming-tips.md)。)  
  
|问题|可能的原因|  
|-------------|--------------------|  
|获取一个消息框显示你的程序导致保护冲突。|许多 Win32 编程错误导致保护冲突。 保护冲突的常见原因是间接分配到 null 指针的数据。 因为这会导致程序尝试访问不属于它的内存，则会发出保护冲突。<br /><br /> 检测保护冲突的原因的简单办法是编译您的程序与调试信息并运行通过 Visual c + + 环境中的调试器。 当保护错误发生时，Windows 将控制权转交给调试器，并将光标置于引起问题的行。|  
|你的程序会生成大量的编译和链接错误。|编译器的警告级别设置为其最大的值之一，并注意警告消息，可以消除许多潜在的问题。 通过使用级别 3 和等级 4 警告级别选项，则可以检测到意外的数据转换、 缺少函数原型，以及使用非 ANSI 功能。|  
  
## <a name="see-also"></a>另请参阅  
 [使用 C 和 Win32 进行多线程编程](../parallel/multithreading-with-c-and-win32.md)