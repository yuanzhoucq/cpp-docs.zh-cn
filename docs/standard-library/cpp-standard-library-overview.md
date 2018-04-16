---
title: "C++ 标准库概述 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- headers, C++ library
- C++ Standard Library
- libraries, Standard C++
- C++ Standard Library, headers
ms.assetid: 7acb83a4-da73-4ad3-bc30-a71289db7f60
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2892f3df9375a220902588ff37e73c5b9e8b1719
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="c-standard-library-overview"></a>C++ 标准库概述
所有 C++ 库实体都在在一个或多个标准标头中声明或定义。 此实现包括 C++ 标准版不需要的两个额外标头：`<hash_map>` 和 `<hash_set>`。 有关此实现支持的标头的完整列表，请参阅[头文件参考](../standard-library/cpp-standard-library-header-files.md)。  
  
 C++ 库的独立式实现仅提供了这些标头的一个子集：  
  
|||  
|-|-|  
|[\<cstddef>](../standard-library/cstddef.md)|[\<cstdlib>](../standard-library/cstdlib.md)（至少声明函数 `abort`、`atexit` 和 `exit`）|  
|[\<exception>](../standard-library/exception.md)|[\<limits>](../standard-library/limits.md)|  
|[\<new>](../standard-library/new.md)|[\<cstdarg>](../standard-library/cstdarg.md)|  
  
 C++ 库标头有两个更广泛的细分：  
  
-   [iostreams](../standard-library/iostreams-conventions.md) 约定。  
  
-   [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)约定。  
  
 本节包含以下部分：  
  
-   [使用 C++ 库标头](../standard-library/using-cpp-library-headers.md)  
  
-   [C++ 库约定](../standard-library/cpp-library-conventions.md)  
  
-   [iostreams 约定](../standard-library/iostreams-conventions.md)  
  
-   [C++ 程序启动和终止](../standard-library/cpp-program-startup-and-termination.md)  
  
-   [安全库：C++ 标准库](../standard-library/safe-libraries-cpp-standard-library.md)  
  
-   [经检查的迭代器](../standard-library/checked-iterators.md)  
  
-   [Debug Iterator Support](../standard-library/debug-iterator-support.md)  
  
-   [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)  
  
-   [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)  
  
-   [stdext 命名空间](../standard-library/stdext-namespace.md)  
  
-   [正则表达式 (C++)](../standard-library/regular-expressions-cpp.md)  
  
 有关 Visual C++ 运行时库的详细信息，请参阅 [CRT 库功能](../c-runtime-library/crt-library-features.md)。  
  
## <a name="see-also"></a>请参阅  
 [C++ 标准库](../standard-library/cpp-standard-library-reference.md)

