---
title: 了解 C/C++ 程序的清单生成
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
ms.assetid: a1f24221-5b09-4824-be48-92eae5644b53
ms.openlocfilehash: 16d5efc5c5f7ce81b4b60269b0c666fd5d24266e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492526"
---
# <a name="understanding-manifest-generation-for-cc-programs"></a>了解 C/C++ 程序的清单生成

[清单](/windows/win32/sbscs/manifests)是一个 xml 文档, 可以是外部 XML 文件或嵌入在应用程序或程序集内的资源。 [独立应用程序](/windows/win32/SbsCs/isolated-applications)的清单用于管理共享的并行程序集的名称和版本, 应用程序应当在运行时绑定到这些程序集。 并行程序集的清单指定其对名称、版本、资源和其他程序集的依赖关系。

可以通过两种方式为独立应用程序或并行程序集创建清单。 首先, 程序集的作者可以按照规则和命名要求手动创建清单文件。 或者, 如果程序仅依赖于 Visual C++程序集 (如 CRT、MFC、ATL 或其他程序), 则链接器可以自动生成清单。

可视化C++库的标头包含程序集信息, 在应用程序代码中包括库时, 链接器将使用此程序集信息来形成最终二进制文件的清单。 链接器不会将清单文件嵌入到二进制文件中, 只能将清单生成为外部文件。 将清单作为外部文件可能不适用于所有方案。 例如, 建议私有程序集具有嵌入的清单。 在命令行生成 (如使用 nmake 生成代码的命令行生成) 中, 可以使用清单工具嵌入清单;有关详细信息, 请参阅[命令行上的清单生成](manifest-generation-at-the-command-line.md)。 在 Visual Studio 中生成时, 可以通过在 "**项目属性**" 对话框中设置清单工具的属性来嵌入清单;请参阅[Visual Studio 中的清单生成](manifest-generation-in-visual-studio.md)。

## <a name="see-also"></a>请参阅

[独立应用程序和并行程序集的概念](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[生成 C/C++ 独立应用程序和并行程序集](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
