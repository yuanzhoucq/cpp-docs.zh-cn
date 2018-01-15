---
title: "&lt;ccomplex&gt; | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <ccomplex>
dev_langs: C++
ms.assetid: a9fcb5f0-88e3-464b-a5fd-d1afb8cd7e6f
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c381a68e913be77a1d62dc0f90fecdca9ee8d226
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ltccomplexgt"></a>&lt;ccomplex&gt;
包含 C++ 标准库标头 [\<complex>](../standard-library/complex.md)，它可有效地包含标准 C 库标头 \<complex.h>，并将关联名称添加到 `std` 命名空间。  
  
## <a name="syntax"></a>语法  
  
```cpp  
#include <ccomplex>  
  
```  
  
## <a name="remarks"></a>备注  
 包含该标头还将确保使用标准 C 库标头中的外部链接声明的名称在 `std` 命名空间中声明。  
  
 未在 `std` 命名空间中定义 \<complex.h> 中声明的名称 `clog`，因为这可能会与 [\<iostream>](../standard-library/iostream.md) 中声明的 `clog` 发生冲突。  
  
## <a name="see-also"></a>请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 标准库概述](../standard-library/cpp-standard-library-overview.md)



