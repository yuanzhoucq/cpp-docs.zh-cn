---
title: 生成 C/C++ 独立应用程序
ms.date: 11/04/2016
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
ms.openlocfilehash: f550125c9e7dcbddcd992652dff7fd23824eeec8
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413025"
---
# <a name="building-cc-isolated-applications"></a>生成 C/C++ 独立应用程序

独立应用程序仅取决于通过并行程序集，并将绑定到使用清单及其依赖项。 这不是必需的应用程序以完全隔离要在 Windows; 上正确运行但是，通过投资使你完全隔离的应用程序，可能会节省时间如果你需要服务在将来，你的应用程序。 使应用程序完全独立的优势详细信息，请参阅[独立应用程序](/windows/desktop/SbsCs/isolated-applications)。

生成使用 Visual c + + 本机 C/c + + 应用程序时，则在默认情况下，Visual Studio 项目系统将生成描述 Visual c + + 库上的应用程序的依赖项的清单文件。 如果这些是唯一的依赖项应用程序就会具有，则它将成为独立应用程序，只要它使用 Visual Studio 重新生成。 如果你的应用程序在运行时，使用其他库，则可能需要重新为通过并行程序集生成这些库[生成 C/c + +-并行程序集](../build/building-c-cpp-side-by-side-assemblies.md)。

## <a name="see-also"></a>请参阅

[独立应用程序和并行程序集的概念](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[生成 C/C++ 独立应用程序和并行程序集](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
