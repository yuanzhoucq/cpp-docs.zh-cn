---
title: OpenMP 库参考
ms.date: 12/02/2019
ms.assetid: a25188c6-edde-43d0-84b5-780e797b08fc
ms.openlocfilehash: b61eb356b782b3cd17557827734a706e0761a2a8
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810749"
---
# <a name="openmp-library-reference"></a>OpenMP 库参考

提供 OpenMP API 中使用的构造的链接。

OpenMP 标准C++的可视化实现包括以下构造。

|构造|描述|
|---------------|-----------------|
|[指令](openmp-directives.md)|提供 OpenMP API 中使用的指令的链接。|
|[子句](openmp-clauses.md)|提供 OpenMP API 中使用的子句的链接。|
|[函数](openmp-functions.md)|提供 OpenMP API 中使用的函数的链接。|
|[环境变量](openmp-environment-variables.md)|提供 OpenMP API 中使用的环境变量的链接。|

Visual C++ OpenMP 运行时库函数包含在以下库中。

|OpenMP 运行时库|特征|
|------------------------------|---------------------|
|VCOMP.LIB|多线程、动态链接（VCOMP140 的导入库。DLL）。|
|VCOMPD.LIB|多线程、动态链接（VCOMP140D 的导入库。DLL）（调试）|

如果 _DEBUG 在编译中定义，并且 `#include <omp.h>` 在源代码中，则为 VCOMPD。LIB 将是默认的 lib，否则为 VCOMP。将使用 LIB。

可以使用[/NODEFAULTLIB （忽略库）](../../../build/reference/nodefaultlib-ignore-libraries.md)删除默认的 lib，并显式链接到所选的 lib。

OpenMP Dll 位于 Visual C++可再发行目录中，需要与使用 OpenMP 的应用程序一起分发。

## <a name="see-also"></a>另请参阅

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)
