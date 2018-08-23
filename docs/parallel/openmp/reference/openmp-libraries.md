---
title: OpenMP 库 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: f89abf97-67e3-4327-bc30-43f85b9533a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 46bd287ff8a020a4d5d7775afdb12f5571d43294
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694766"
---
# <a name="openmp-libraries"></a>OpenMP 库
讨论构成 Visual c + + 中的 OpenMP 运行时库的.lib 文件。  
  
 以下库包含 Visual c + + OpenMP 运行时库函数。  
  
|OpenMP 运行时库|特征|  
|------------------------------|---------------------|  
|VCOMP.LIB|多线程，动态链接 （VCOMP 导入库。LIB)。|  
|VCOMPD.LIB|多线程，动态链接 （VCOMPD 导入库。合上盖子） （调试）|  
  
 如果在一次编译中定义 _DEBUG 并且`#include omp.h`在源代码，VCOMPD。LIB 将默认 lib。 否则为 VCOMP。将使用 LIB。  
  
 你可以使用[/NODEFAULTLIB （忽略库）](../../../build/reference/nodefaultlib-ignore-libraries.md)删除默认 lib 并显式链接到与所选的 lib。  
  
 OpenMP Dll 中的 Visual c + + 可再发行组件目录，并且需要随应用程序使用 OpenMP 一起分发。  
  
## <a name="see-also"></a>请参阅  
 [库参考](../../../parallel/openmp/reference/openmp-library-reference.md)