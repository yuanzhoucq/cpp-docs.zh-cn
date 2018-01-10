---
title: "stdin、stdout、stderr | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- stdin
- stderr
- stdout
dev_langs: C++
helpviewer_keywords:
- stdout function
- standard output stream
- standard error stream
- stdin function
- standard input stream
- stderr function
ms.assetid: badd4735-596d-4498-857c-ec8b7e670e4c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7683a0ed1e40a0b65ea3a400c460dcd23ecef2d0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="stdin-stdout-stderr"></a>stdin、stdout、stderr
## <a name="syntax"></a>语法  
  
```  
  
      FILE *stdin;   
FILE *stdout;   
FILE *stderr;   
#include <stdio.h>  
```  
  
## <a name="remarks"></a>备注  
 以下是输入、输出和错误输出的标准流。  
  
 默认情况下，标准输入是从键盘读取的，而标准输出和错误输出将打印到屏幕。  
  
 下列流指针可用于访问标准流：  
  
|指针|流|  
|-------------|------------|  
|`stdin`|标准输入|  
|**stdout**|标准输出|  
|`stderr`|标准错误|  
  
 这些指针可用作函数自变量。 一些函数（如 getchar 和 `putchar`）将自动使用 `stdin` 和 stdout。  
  
 这些指针是常量，无法分配新的值。 `freopen` 函数可用于将流重定向到磁盘文件或其他设备。 操作系统使您可以在命令级别重定向程序的标准输入和输出。  
  
## <a name="see-also"></a>请参阅  
 [流 I/O](../c-runtime-library/stream-i-o.md)   
 [全局常量](../c-runtime-library/global-constants.md)