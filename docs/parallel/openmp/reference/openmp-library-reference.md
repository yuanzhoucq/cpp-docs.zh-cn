---
title: OpenMP 库参考
ms.date: 07/30/2019
ms.assetid: a25188c6-edde-43d0-84b5-780e797b08fc
ms.openlocfilehash: c78c2677741714ab48d49a4443ad753369ec4500
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/31/2019
ms.locfileid: "68682595"
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
|VCOMP.LIB|多线程、动态链接 (VCOMP 的导入库。LIB)。|
|VCOMPD.LIB|多线程、动态链接 (VCOMPD 的导入库。盖子) (调试)|

如果在编译中定义`#include omp.h`了 _debug 并且在源代码中为 VCOMPD, 则为。LIB 将是默认的 lib, 否则为 VCOMP。将使用 LIB。

可以使用[/NODEFAULTLIB (忽略库)](../../../build/reference/nodefaultlib-ignore-libraries.md)删除默认的 lib, 并显式链接到所选的 lib。

OpenMP Dll 位于 Visual C++可再发行目录中, 需要与使用 OpenMP 的应用程序一起分发。

## <a name="see-also"></a>请参阅

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)