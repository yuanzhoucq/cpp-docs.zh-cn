---
title: 生成 C/C++ 独立应用程序
ms.date: 05/06/2019
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
ms.openlocfilehash: fbb553e3514ac3c32ee1e1f276dcb3e43d3a192e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493348"
---
# <a name="building-cc-isolated-applications"></a>生成 C/C++ 独立应用程序

独立的应用程序仅依赖于并排程序集，并使用清单绑定到其依赖项。 你不必完全隔离应用程序，以便其在 Windows 上正常运行；但如果将来需要维护应用程序，则可通过完全隔离应用程序来节省时间。 有关完全隔离应用程序的优点的更多信息，请参阅[独立的应用程序](/windows/win32/SbsCs/isolated-applications)。

使用 Visual Studio 生成本地 C/C++ 应用程序时，默认情况下 Visual Studio 项目系统会生成清单文件，用于描述应用程序对 Visual Studio 库的依赖关系。 如果这些依赖关系是应用程序所具有的独特依赖关系，则只要应用程序是使用 Visual Studio 重新生成的，它就会成为独立的应用程序。 如果应用程序在运行时使用其他库，则可能需要按照[生成 C/C++ 并行程序集](building-c-cpp-side-by-side-assemblies.md)中所描述的步骤将这些库重新生成为并行程序集。

## <a name="see-also"></a>请参阅

[独立应用程序和并行程序集的概念](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[生成 C/C++ 独立应用程序和并行程序集](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
