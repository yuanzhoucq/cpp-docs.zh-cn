---
title: 了解 C/C++ 程序的清单生成
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
ms.assetid: a1f24221-5b09-4824-be48-92eae5644b53
ms.openlocfilehash: ff8d9f214b4fe4d004691c54474dcdabf2c0af85
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314736"
---
# <a name="understanding-manifest-generation-for-cc-programs"></a>了解 C/C++ 程序的清单生成

一个[清单](/windows/desktop/sbscs/manifests)嵌入到应用程序或程序集可以是外部 XML 文件或资源的 XML 文档。 清单[独立应用程序](/windows/desktop/SbsCs/isolated-applications)用于管理的名称和版本的应用程序应在运行时绑定到共享的并行程序集。 通过并行程序集清单指定名称、 版本、 资源和其他程序集及其依赖项。

有两种方法来创建独立应用程序或通过并行程序集清单。 首先，该程序集的作者可以手动创建以下规则和命名要求的清单文件。 或者，如果某个程序仅依赖于视觉对象C++链接器可以自动生成如 CRT、 MFC、 ATL 或其他人，则清单的程序集。

视觉对象的标头C++库包含程序集信息和这些库包含在应用程序代码中，当使用此程序集信息由链接器以形成最终二进制文件的清单。 链接器不会嵌入二进制文件中，在清单文件，并只能生成清单中的，作为外部文件。 作为外部文件具有一个清单可能不适用于所有方案。 例如，建议使用专用程序集嵌入了清单。 在命令行生成，如那些使用 nmake 来生成代码，清单可以嵌入使用清单工具;有关详细信息请参阅[在命令行的清单生成](manifest-generation-at-the-command-line.md)。 构建时 Visual Studio 中，可以通过设置中的清单工具属性嵌入清单**项目属性**对话框，请参见[在 Visual Studio 中的清单生成](manifest-generation-in-visual-studio.md)。

## <a name="see-also"></a>请参阅

[独立应用程序和并行程序集的概念](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[生成 C/C++ 独立应用程序和并行程序集](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
