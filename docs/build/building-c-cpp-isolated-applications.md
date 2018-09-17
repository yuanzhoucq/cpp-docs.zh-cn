---
title: 生成 C/c + + 独立应用程序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78d14f812700afa4ea0ad66b527a0e3888862f4d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716895"
---
# <a name="building-cc-isolated-applications"></a>生成 C/C++ 独立应用程序

独立应用程序仅取决于通过并行程序集，并将绑定到使用清单及其依赖项。 这不是必需的应用程序以完全隔离要在 Windows; 上正确运行但是，通过投资使你完全隔离的应用程序，可能会节省时间如果你需要服务在将来，你的应用程序。 使应用程序完全独立的优势详细信息，请参阅[独立应用程序](/windows/desktop/SbsCs/isolated-applications)。

生成使用 Visual c + + 本机 C/c + + 应用程序时，则在默认情况下，Visual Studio 项目系统将生成描述 Visual c + + 库上的应用程序的依赖项的清单文件。 如果这些是唯一的依赖项应用程序就会具有，则它将成为独立应用程序，只要它使用 Visual Studio 重新生成。 如果你的应用程序在运行时，使用其他库，则可能需要重新为通过并行程序集生成这些库[生成 C/c + +-并行程序集](../build/building-c-cpp-side-by-side-assemblies.md)。

## <a name="see-also"></a>请参阅

[独立应用程序和并行程序集的概念](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[生成 C/C++ 独立应用程序和并行程序集](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)