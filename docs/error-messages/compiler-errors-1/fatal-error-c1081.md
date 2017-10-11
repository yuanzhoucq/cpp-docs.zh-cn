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
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 148e3e6035304eb155a478e5971defd9a0a55120
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="fatal-error-c1081"></a>错误 C1081
symbol： 文件名太长  
  
 文件的路径名的长度超过`_MAX_PATH`（由 stdlib.h 定义为 260 个字符）。 缩短文件的名称。  
  
 如果用短文件名调用 CL.exe，编译器可能需要生成完整的路径名。 例如，`cl -c myfile.cpp`可能会导致编译器生成：  
  
```  
D:\<very-long-directory-path>\myfile.cpp  
```
