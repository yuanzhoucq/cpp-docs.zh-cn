---
title: 自动化服务器： 对象生存期问题 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- objects [MFC], lifetime
- lifetime, automation server
- Automation servers, object lifetime
- servers, lifetime of Automation
ms.assetid: 342baacf-4015-4a0e-be2f-321424f1cb43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a53d1a9d3849798fa1e583c0758b156d282a401c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397112"
---
# <a name="automation-servers-object-lifetime-issues"></a>自动化服务器：对象生存期问题

当自动化客户端创建或激活一个 OLE 项时，服务器会向客户端传递一个指向该对象的指针。 客户端将建立对通过调用 OLE 函数对象的引用[iunknown:: Addref](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref)。 此引用直到客户端调用实际上是[iunknown:: Release](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release)。 （使用 Microsoft 基础类库类的 OLE 类编写的客户端应用程序不需要执行这些调用；框架也是如此。）OLE 系统和服务器本身可能会建立对对象的引用。 只要对某个对象的外部引用仍然有效，服务器就不应销毁该对象。

框架维护对派生自任何服务器对象的引用数的内部计数[CCmdTarget](../mfc/reference/ccmdtarget-class.md)。 当自动化客户端或其他实体添加或释放对对象的引用时，将更新此计数。

引用计数变为 0 时，框架将调用虚函数[ccmdtarget:: Onfinalrelease](../mfc/reference/ccmdtarget-class.md#onfinalrelease)。 此函数的默认实现调用**删除**运算符来删除此对象。

当外部客户端具有对应用程序的对象的引用时，Microsoft 基础类库提供用于控制应用程序行为的附加工具。 除了维护对每个对象的引用的计数之外，服务器还维护活动对象的全局计数。 全局函数[AfxOleLockApp](../mfc/reference/application-control.md#afxolelockapp)并[AfxOleUnlockApp](../mfc/reference/application-control.md#afxoleunlockapp)更新应用程序的活动对象计数。 如果此计数不为零，则在用户从系统菜单中选择“关闭”或从“文件”菜单中选择“退出”时，应用程序不会终止。 相反，应用程序的主窗口将隐藏（但不销毁），直到完成所有等待的客户端请求。 通常，分别在支持自动化的类的构造函数和析构函数中调用 `AfxOleLockApp` 和 `AfxOleUnlockApp`。

有时，某些情况会迫使服务器终止，但客户端仍具有对某个对象的引用。 例如，服务器依赖的资源可能变得不可用，从而导致服务器遇到错误。 用户也可能关闭包含了其他应用程序引用的对象的服务器文档。

在 Windows SDK 中，请参阅`IUnknown::AddRef`和`IUnknown::Release`。

## <a name="see-also"></a>请参阅

[自动化服务器](../mfc/automation-servers.md)<br/>
[AfxOleCanExitApp](../mfc/reference/application-control.md#afxolecanexitapp)

