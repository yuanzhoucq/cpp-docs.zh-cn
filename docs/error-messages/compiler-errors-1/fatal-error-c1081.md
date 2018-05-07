---
title: 错误 C1081 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1081
dev_langs:
- C++
helpviewer_keywords:
- C1081
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b5ea18ff3f2714d9621d4372cf541be2f9b225a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1081"></a>错误 C1081
symbol： 文件名太长  
  
 文件的路径名的长度超过`_MAX_PATH`（由 stdlib.h 定义为 260 个字符）。 缩短文件的名称。  
  
 如果用短文件名调用 CL.exe，编译器可能需要生成完整的路径名。 例如，`cl -c myfile.cpp`可能会导致编译器生成：  
  
```  
D:\<very-long-directory-path>\myfile.cpp  
```