---
title: 针对 MFC 模块状态中的激活上下文的支持
ms.date: 11/04/2016
helpviewer_keywords:
- activation contexts [MFC]
- activation contexts [MFC], MFC support
ms.assetid: 1e49eea9-3620-46dd-bc5f-d664749567c7
ms.openlocfilehash: a2e5f56eeb323f1bd5f20c5920bbdbe4a658554d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306660"
---
# <a name="support-for-activation-contexts-in-the-mfc-module-state"></a>针对 MFC 模块状态中的激活上下文的支持

MFC 使用用户模块提供的清单资源创建激活上下文。 有关如何创建激活上下文的详细信息，请参阅下列主题：

- [激活上下文](/windows/desktop/SbsCs/activation-contexts)

- [应用程序清单](/windows/desktop/SbsCs/application-manifests)

- [程序集清单](/windows/desktop/SbsCs/assembly-manifests)

## <a name="remarks"></a>备注

在读取这些 Windows SDK 主题，请注意，MFC 激活上下文机制类似 Windows SDK 的激活上下文，只不过 MFC 不使用 Windows SDK 激活上下文 API。

按以下方式将激活上下文的工作方式在 MFC 应用程序、 用户 Dll 和 MFC 扩展 Dll:

- MFC 应用程序为其清单资源使用资源 ID 1。 在这种情况下，MFC 不会创建其自己的激活上下文，但将使用默认应用程序上下文。

- MFC 用户 DLL 为其清单资源使用资源 ID 2。 此时，MFC 将为每用户 DLL 创建激活上下文，以便其他用户 DLL 可使用同一库（例如，公共控件库）的不同版本。

- MFC 扩展 DLL 依赖其承载应用程序或用户 DLL 建立其激活上下文。

尽管可以使用下描述的过程修改激活上下文状态[使用激活上下文 API](/windows/desktop/SbsCs/using-the-activation-context-api)，使用 MFC 激活上下文机制时非常有用开发基于 DLL 的插件体系结构它不是简单 （或不可能） 单独调用外部插件前后手动切换激活状态。

在中创建激活上下文[AfxWinInit](../mfc/reference/application-information-and-management.md#afxwininit)。 它将在 `AFX_MODULE_STATE` 析构函数中销毁。 激活上下文句柄保留在 `AFX_MODULE_STATE` 中。 (`AFX_MODULE_STATE`中所述[AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)。)

[AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state)宏激活和停用激活上下文。 将为静态 MFC 库以及 MFC DLL 启用 `AFX_MANAGE_STATE`，以使 MFC 代码在用户 DLL 选择的正确激活上下文中执行。

## <a name="see-also"></a>请参阅

[激活上下文](/windows/desktop/SbsCs/activation-contexts)<br/>
[应用程序清单](/windows/desktop/SbsCs/application-manifests)<br/>
[程序集清单](/windows/desktop/SbsCs/assembly-manifests)<br/>
[AfxWinInit](../mfc/reference/application-information-and-management.md#afxwininit)<br/>
[AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)<br/>
[AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state)
