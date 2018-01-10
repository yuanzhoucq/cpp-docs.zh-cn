---
title: "OpenMP 库 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: f89abf97-67e3-4327-bc30-43f85b9533a2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5c0f009c26789fd771d55dab5fcfe5f342aa03b1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="openmp-libraries"></a>OpenMP 库
讨论构成 Visual c + + 中的 OpenMP 运行时库的.lib 文件。  
  
 以下库包含 Visual c + + OpenMP 运行时库函数。  
  
|OpenMP 运行时库|特征|  
|------------------------------|---------------------|  
|VCOMP。LIB|多线程，动态链接 （VCOMP 导入库。LIB)。|  
|VCOMPD。LIB|多线程，动态链接 （VCOMPD 导入库。合上盖子） （调试）|  
  
 如果在一次编译中定义 _DEBUG 并且`#include omp.h`在源代码，VCOMPD。LIB 将默认 lib。 否则为 VCOMP。将使用 LIB。  
  
 你可以使用[/NODEFAULTLIB （忽略库）](../../../build/reference/nodefaultlib-ignore-libraries.md)删除默认 lib 并显式链接到与所选的 lib。  
  
 OpenMP Dll 中的 Visual c + + 可再发行组件目录，并且需要随应用程序使用 OpenMP 一起分发。  
  
## <a name="see-also"></a>请参阅  
 [库参考](../../../parallel/openmp/reference/openmp-library-reference.md)