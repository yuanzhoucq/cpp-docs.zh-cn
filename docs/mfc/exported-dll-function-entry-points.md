---
title: 导出的 DLL 函数入口点
ms.date: 11/04/2016
helpviewer_keywords:
- exporting DLLs [MFC], functions
- MFC, managing state data
- state management [MFC], exported DLLs
ms.assetid: 3268666e-d24b-44f2-80e8-7c80f73b93ca
ms.openlocfilehash: c521cad666864c728fd871b460cf0c92b815e414
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622643"
---
# <a name="exported-dll-function-entry-points"></a>导出的 DLL 函数入口点

对于 DLL 的导出函数，请使用[AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state)宏在从 DLL 模块切换到调用应用程序的 dll 时维持适当的全局状态。

调用时，此宏会针对函数包含范围的其余部分，将 `pModuleState`（一个指向包含模块的全局数据的 `AFX_MODULE_STATE` 结构的指针）设置为有效的模块状态。 一旦离开包含宏的范围，之前的有效模块状态将会自动还原。

此切换通过在堆栈上构造类的实例来实现 `AFX_MODULE_STATE` 。 在构造函数中，此类获取一个指向当前模块状态的指针并将其存储在一个成员变量中，然后将 `pModuleState` 设置为新的有效模块状态。 在析构函数中，此类将还原存储在其成员变量中的指针作为有效的模块状态。

如果有一个导出的函数，例如在 DLL 中启动对话框的函数，则需要将以下代码添加到函数的开头：

[!code-cpp[NVC_MFCConnectionPoints#6](codesnippet/cpp/exported-dll-function-entry-points_1.cpp)]

这会将当前模块状态替换为从[AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)返回的状态，直到当前范围结束。

如果未使用 `AFX_MANAGE_STATE` 宏，则 DLL 中将产生资源问题。 默认情况下，MFC 使用主应用程序的资源句柄来加载资源模板。 此模板实际存储在 DLL 中。 根本原因是 `AFX_MANAGE_STATE` 宏尚未切换 MFC 的模块状态信息。 资源句柄将从 MFC 的模块状态中恢复。 不切换模块状态将导致使用错误的资源句柄。

`AFX_MANAGE_STATE` 不需要放置到 DLL 中的每个函数中。 例如，`InitInstance` 可由应用程序中的 MFC 代码调用，而无需 `AFX_MANAGE_STATE`，因为 MFC 会在 `InitInstance` 之前自动切换模块状态，然后在 `InitInstance` 返回之后将其切换回来。 上述情况同样适用于所有消息映射处理程序。 在路由任何消息之前，普通 MFC Dll 实际上有一个特殊的主窗口过程，该过程会自动切换模块状态。

## <a name="see-also"></a>另请参阅

[管理 MFC 模块的状态数据](managing-the-state-data-of-mfc-modules.md)
