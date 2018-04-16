---
title: "输入和输出 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.io
dev_langs:
- C++
helpviewer_keywords:
- input routines
- I/O [CRT]
- I/O routines
- I/O [CRT], routines
- output routines
ms.assetid: 1c177301-e341-4ca0-aedc-0a87fe1c75ae
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 35e97e7bbbc04699e813b6890180512043c4e25d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="input-and-output"></a>输入和输出
I/O 函数在文件和设备中读取和写入数据。 文件 I/O 操作在文本模式或二进制模式下进行。 Microsoft 运行库有三种类型的 I/O 函数：  
  
-   [流 I/O](../c-runtime-library/stream-i-o.md) 函数将数据视为单个字符的流。  
  
-   [低级别 I/O](../c-runtime-library/low-level-i-o.md) 函数将为低于流 I/O 提供的操作的低级别操作直接调用操作系统。  
  
-   [控制台和端口 I/O](../c-runtime-library/console-and-port-i-o.md) 函数直接在控制台（键盘和屏幕）或 I/O 端口（如打印机端口）中进行读取和写入。  
  
    > [!NOTE]
    >  由于流函数将进行缓冲而底层函数不会这样，因此这两种类型的函数通常是不兼容的。 若要处理特定文件，请以独占方式使用流函数或底层函数。  
  
## <a name="see-also"></a>请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)