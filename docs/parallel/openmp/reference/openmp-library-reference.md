---
title: OpenMP 库参考
ms.date: 03/20/2019
ms.assetid: a25188c6-edde-43d0-84b5-780e797b08fc
ms.openlocfilehash: 6f4bbeca54bff1fc44a3576362edca9c30926d5a
ms.sourcegitcommit: 14b292596bc9b9b883a9c58cd3e366b282a1f7b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2019
ms.locfileid: "60124689"
---
# <a name="openmp-library-reference"></a>OpenMP 库参考

提供指向 OpenMP API 中使用的构造。

视觉对象C++实现的 OpenMP 标准还包括以下构造。

|构造|描述|
|---------------|-----------------|
|[指令](openmp-directives.md)|提供指向 OpenMP API 中使用的指令。|
|[子句](openmp-directives.md)|提供指向子句在 OpenMP API 中使用。|
|[函数](openmp-functions.md)|提供指向 OpenMP API 中使用的函数。|
|[环境变量](openmp-environment-variables.md)|提供指向 OpenMP API 中使用的环境变量。|

视觉对象C++OpenMP 运行时库函数都包含在以下库。

|OpenMP 运行时库|特征|
|------------------------------|---------------------|
|VCOMP.LIB|多线程、 动态链接 （VCOMP 导入库。LIB)。|
|VCOMPD.LIB|多线程、 动态链接 （VCOMPD 导入库。合上盖子） （调试）|

如果在编译时定义 _DEBUG 并且如果`#include omp.h`是源代码，VCOMPD 中。LIB 将默认 lib，否则为 VCOMP。将使用 LIB。

可以使用[/NODEFAULTLIB （忽略库）](../../../build/reference/nodefaultlib-ignore-libraries.md)若要删除默认 lib 并显式链接到与所选的库。

OpenMP Dll 是视觉对象中C++可再发行组件的目录并需要随使用 OpenMP 的应用程序一起分发。

## <a name="see-also"></a>请参阅

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)