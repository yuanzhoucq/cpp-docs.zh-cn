---
title: 生成 C/C++ 独立应用程序
ms.date: 05/06/2019
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
ms.openlocfilehash: fbb553e3514ac3c32ee1e1f276dcb3e43d3a192e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493348"
---
# <a name="building-cc-isolated-applications"></a>生成 C/C++ 独立应用程序

独立的应用程序仅依赖于并行程序集, 并使用清单绑定到其依赖项。 为了在 Windows 上正常运行, 无需完全隔离应用程序;但是, 如果你需要在将来为应用程序服务, 则可以通过投资使应用程序完全隔离, 来节省时间。 有关使应用程序完全隔离的优点的详细信息, 请参阅[独立应用程序](/windows/win32/SbsCs/isolated-applications)。

使用 Visual Studio 生成本机 C/C++应用程序时, 默认情况下, Visual studio 项目系统会生成一个清单文件, 用于描述应用程序在 Visual studio 库中的依赖关系。 如果这些是你的应用程序所具有的唯一依赖项, 则在使用 Visual Studio 重新生成该应用程序后, 它将成为独立的应用程序。 如果你的应用程序在运行时使用其他库, 则你可能需要按照[生成 C/C++并行程序集](building-c-cpp-side-by-side-assemblies.md)中所述的步骤, 将这些库重新生成为并行程序集。

## <a name="see-also"></a>请参阅

[独立应用程序和并行程序集的概念](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[生成 C/C++ 独立应用程序和并行程序集](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
