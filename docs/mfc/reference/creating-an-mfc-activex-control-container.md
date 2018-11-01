---
title: 创建 MFC ActiveX 控件容器
ms.date: 09/12/2018
f1_keywords:
- vc.appwiz.activex.container
helpviewer_keywords:
- MFC ActiveX controls [MFC], containers
- ActiveX control containers [MFC], creating
- containers [MFC], creating
- OLE controls [MFC], containers
ms.assetid: ec70e137-7c14-4940-bd0e-fd4edcc63ea5
ms.openlocfilehash: 04c271db18bc8d8ba273f16f7493bbbb1da96421
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544984"
---
# <a name="creating-an-mfc-activex-control-container"></a>创建 MFC ActiveX 控件容器

ActiveX 控件容器是一个父程序，提供 ActiveX (以前称为 OLE) 控件运行环境。 您可以创建应用程序能够包含 ActiveX 控件或无需 MFC，但很容易做到与 MFC。

>[!IMPORTANT]
> ActiveX 是一项传统技术，不应使用新的开发。 有关取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](../activex-controls.md)。

创建 MFC 容器程序使用[MFC 应用程序向导](../../mfc/reference/mfc-application-wizard.md)可用于访问由 MFC 和 ActiveX 类实现的许多 ActiveX 控件和自动化功能。 这些功能包括可视化编辑，自动化，创建复合文件，以及支持的控件。 父程序支持的 MFC 应用程序向导可视化编辑选项包括创建容器、 最小化服务器、 完全服务器和容器和服务器的程序。

- **新的 MFC 应用程序**。 若要创建新的 MFC 程序，包括自动化，可视化编辑复合文件，或控制支持、 使用 MFC 应用程序向导并选择相应的自动化选项。

- **现有 MFC 应用程序**。 如果将控件包含添加到现有 MFC 应用程序，请参阅[OLE 控件容器： 手动启用 OLE 控件包容](../../mfc/activex-control-containers-manually-enabling-activex-control-containment.md)。

### <a name="to-create-an-activex-container-for-any-of-the-following-types-of-applications"></a>若要创建以下类型的应用程序的任何一个 ActiveX 容器

1. [容器](../../mfc/containers.md)

1. [可视化编辑](../../mfc/ole-mfc.md)

1. [MFC ActiveX 控件](../../mfc/mfc-activex-controls.md)

## <a name="see-also"></a>请参阅

[Visual C++ 项目类型](../../ide/visual-cpp-project-types.md)

