---
title: 针对 MFC 模块状态中的激活上下文的支持
ms.date: 11/04/2016
helpviewer_keywords:
- activation contexts [MFC]
- activation contexts [MFC], MFC support
ms.assetid: 1e49eea9-3620-46dd-bc5f-d664749567c7
ms.openlocfilehash: 296df3d2ecec74c5c9a7deef1617298d40243724
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511429"
---
# <a name="support-for-activation-contexts-in-the-mfc-module-state"></a>针对 MFC 模块状态中的激活上下文的支持

MFC 使用用户模块提供的清单资源创建激活上下文。 有关如何创建激活上下文的详细信息，请参阅下列主题：

- [激活上下文](/windows/win32/SbsCs/activation-contexts)

- [应用程序清单](/windows/win32/SbsCs/application-manifests)

- [程序集清单](/windows/win32/SbsCs/assembly-manifests)

## <a name="remarks"></a>备注

阅读这些 Windows SDK 主题时, 请注意 MFC 激活上下文机制类似于 Windows SDK 激活上下文, 但 MFC 不使用 Windows SDK 激活上下文 API。

激活上下文在 MFC 应用程序、用户 Dll 和 MFC 扩展 Dll 中的工作方式如下:

- MFC 应用程序为其清单资源使用资源 ID 1。 在这种情况下，MFC 不会创建其自己的激活上下文，但将使用默认应用程序上下文。

- MFC 用户 DLL 为其清单资源使用资源 ID 2。 此时，MFC 将为每用户 DLL 创建激活上下文，以便其他用户 DLL 可使用同一库（例如，公共控件库）的不同版本。

- MFC 扩展 DLL 依赖其承载应用程序或用户 DLL 建立其激活上下文。

尽管可以使用[激活上下文 API](/windows/win32/SbsCs/using-the-activation-context-api)下所述的过程修改激活上下文状态, 但在开发基于 DLL 的插件体系结构时, 使用 MFC 激活上下文机制可能会很有用 (或不可能) 在对外部插件的单独调用前后手动切换激活状态。

激活上下文是在[AfxWinInit](../mfc/reference/application-information-and-management.md#afxwininit)中创建的。 它将在 `AFX_MODULE_STATE` 析构函数中销毁。 激活上下文句柄保留在 `AFX_MODULE_STATE` 中。 (`AFX_MODULE_STATE`在[AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)中进行了介绍。)

[AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state)宏激活和停用激活上下文。 将为静态 MFC 库以及 MFC DLL 启用 `AFX_MANAGE_STATE`，以使 MFC 代码在用户 DLL 选择的正确激活上下文中执行。

## <a name="see-also"></a>请参阅

[激活上下文](/windows/win32/SbsCs/activation-contexts)<br/>
[应用程序清单](/windows/win32/SbsCs/application-manifests)<br/>
[程序集清单](/windows/win32/SbsCs/assembly-manifests)<br/>
[AfxWinInit](../mfc/reference/application-information-and-management.md#afxwininit)<br/>
[AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)<br/>
[AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state)
