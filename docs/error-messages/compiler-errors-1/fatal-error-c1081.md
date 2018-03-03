---
title: "错误 C1081 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1081
dev_langs:
- C++
helpviewer_keywords:
- C1081
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8bac4aaf0d4aebcbc34f74b6ccb91170fd4224e4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1081"></a>错误 C1081
symbol： 文件名太长  
  
 文件的路径名的长度超过`_MAX_PATH`（由 stdlib.h 定义为 260 个字符）。 缩短文件的名称。  
  
 如果用短文件名调用 CL.exe，编译器可能需要生成完整的路径名。 例如，`cl -c myfile.cpp`可能会导致编译器生成：  
  
```  
D:\<very-long-directory-path>\myfile.cpp  
```