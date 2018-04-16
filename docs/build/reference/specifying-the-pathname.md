---
title: 指定路径名 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- names [C++], compiler output files
- cl.exe compiler, output files
- output files, specifying pathnames
ms.assetid: 7a6595ce-3383-44ae-957a-466bfa29c343
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2412ab15317604e1d6cccc5535226d429d8ba6b7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="specifying-the-pathname"></a>指定路径名
每个输出文件选项接受*路径名*自变量可以指定的位置和输出文件的名称。 自变量可以包括驱动器名称、 目录和文件名称。 不允许有空格选项和自变量之间。  
  
 如果*路径名*包括文件名称不带扩展名，编译器将为输出的默认扩展。 如果*路径名*包括目录却没有文件名称，编译器指定目录中的默认名称创建一个文件。 默认名称基于源文件和基于输出文件的类型的默认扩展的基名称。 如果你离开*路径名*完全，编译器都创建一个文件，默认目录中的默认名称。  
  
 或者，*路径名*自变量可以是设备名称 （AUX、 CON、 PRN，或 NUL），而不是文件名。 不使用选项和设备名称或冒号之间空间的设备名称的一部分。  
  
|设备名称|表示|  
|-----------------|----------------|  
|AUX|辅助设备|  
|CON|控制台|  
|PRN|打印机|  
|NUL|Null 设备 （创建任何文件）|  
  
## <a name="example"></a>示例  
 下面的命令行将发送到打印机的映射文件：  
  
```  
CL /FmPRN HELLO.CPP  
```  
  
## <a name="see-also"></a>请参阅  
 [输出文件 (/ F) 选项](../../build/reference/output-file-f-options.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)