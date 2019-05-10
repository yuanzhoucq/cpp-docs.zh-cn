---
title: 生成 C/C++ 独立应用程序
ms.date: 05/06/2019
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
ms.openlocfilehash: 42192ad9388a8e69b70947c20c6fa7ee428a2bb9
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220968"
---
# <a name="building-cc-isolated-applications"></a>生成 C/C++ 独立应用程序

独立应用程序仅取决于通过并行程序集，并将绑定到使用清单及其依赖项。 这不是必需的应用程序以完全隔离要在 Windows; 上正确运行但是，通过投资使你完全隔离的应用程序，可能会节省时间如果你需要服务在将来，你的应用程序。 使应用程序完全独立的优势详细信息，请参阅[独立应用程序](/windows/desktop/SbsCs/isolated-applications)。

在生成本机 C /C++使用 Visual Studio 中，默认情况下，Visual Studio 项目系统应用程序生成说明了在 Visual Studio 库上的应用程序的依赖项的清单文件。 如果这些是唯一的依赖项应用程序就会具有，则它将成为独立应用程序，只要它使用 Visual Studio 重新生成。 如果你的应用程序在运行时，使用其他库，则可能需要重新为通过并行程序集生成这些库[生成 C /C++通过并行程序集](building-c-cpp-side-by-side-assemblies.md)。

## <a name="see-also"></a>请参阅

[独立应用程序和并行程序集的概念](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[生成 C/C++ 独立应用程序和并行程序集](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
