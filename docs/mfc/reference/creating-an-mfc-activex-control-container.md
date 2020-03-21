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
ms.openlocfilehash: 27f229a23595d4842a77409a3cedc7a57aa43e6c
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079429"
---
# <a name="creating-an-mfc-activex-control-container"></a>创建 MFC ActiveX 控件容器

ActiveX 控件容器是一种父程序，它为要运行的 ActiveX （以前称为 OLE）控件提供环境。 你可以创建一个能够包含带有或不带 MFC 的 ActiveX 控件的应用程序，但使用 MFC 更为简单。

>[!IMPORTANT]
> ActiveX 是一种不能用于新开发的旧技术。 有关取代 ActiveX 的新式技术的详细信息，请参阅[Activex 控件](../activex-controls.md)。

使用[Mfc 应用程序向导](../../mfc/reference/mfc-application-wizard.md)创建 MFC 容器程序允许您访问由 Mfc 和 ActiveX 类实现的 ActiveX 控件和自动化的许多功能。 这些功能包括视觉对象编辑、自动化、创建复合文件和对控件的支持。 父程序将支持的 MFC 应用程序向导可视化编辑选项包括创建容器、小型服务器、完全服务器以及同时作为容器和服务器的程序。

- **新的 MFC 应用程序**。 若要创建一个新的 MFC 程序，该程序包括自动化、可视编辑、复合文件或控件支持，请使用 MFC 应用程序向导并选择相应的自动化选项。

- **现有 MFC 应用程序**。 如果要向现有 MFC 应用程序添加控件包容，请参阅[Ole 控件容器：手动启用 Ole 控件包含](../../mfc/activex-control-containers-manually-enabling-activex-control-containment.md)。

### <a name="to-create-an-activex-container-for-any-of-the-following-types-of-applications"></a>为以下任何类型的应用程序创建 ActiveX 容器

1. [容器](../../mfc/containers.md)

1. [视觉对象编辑](../../mfc/ole-mfc.md)

1. [MFC ActiveX 控件](../../mfc/mfc-activex-controls.md)

## <a name="see-also"></a>另请参阅

[Visual Studio 中的 C++ 项目类型](../../build/reference/visual-cpp-project-types.md)
