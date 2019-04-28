---
title: 生成 C/C++ 独立应用程序
ms.date: 11/04/2016
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
ms.openlocfilehash: e02fec4115d328dd8230d68ddb65b380ec743dc0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274702"
---
# <a name="building-cc-isolated-applications"></a>生成 C/C++ 独立应用程序

独立应用程序仅取决于通过并行程序集，并将绑定到使用清单及其依赖项。 这不是必需的应用程序以完全隔离要在 Windows; 上正确运行但是，通过投资使你完全隔离的应用程序，可能会节省时间如果你需要服务在将来，你的应用程序。 使应用程序完全独立的优势详细信息，请参阅[独立应用程序](/windows/desktop/SbsCs/isolated-applications)。

在生成本机 C /C++应用程序使用视觉对象C++，默认情况下，Visual Studio 项目系统生成的清单文件描述在视觉对象上的应用程序的依赖项C++库。 如果这些是唯一的依赖项应用程序就会具有，则它将成为独立应用程序，只要它使用 Visual Studio 重新生成。 如果你的应用程序在运行时，使用其他库，则可能需要重新为通过并行程序集生成这些库[生成 C /C++通过并行程序集](building-c-cpp-side-by-side-assemblies.md)。

## <a name="see-also"></a>请参阅

[独立应用程序和并行程序集的概念](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[生成 C/C++ 独立应用程序和并行程序集](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
