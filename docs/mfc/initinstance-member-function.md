---
title: InitInstance 成员函数
ms.date: 11/04/2016
f1_keywords:
- InitInstance
helpviewer_keywords:
- InitInstance method [MFC]
- applications [MFC], initializing
- MFC, initializing
- initializing MFC applications
ms.assetid: 4ef09267-ff7f-4c39-91a0-57454a264f83
ms.openlocfilehash: 2cf5b266348e299fe761ba40bd2cfb849f02b9ab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377198"
---
# <a name="initinstance-member-function"></a>InitInstance 成员函数

Windows 操作系统允许您运行同一应用程序的多个副本（也称为“实例”）。 `WinMain`每次应用程序的新实例启动时调用[InitInstance。](../mfc/reference/cwinapp-class.md#initinstance)

MFC 应用程序向导创建的标准 `InitInstance` 实现将执行以下任务：

- 作为其中心操作，将创建文档模板，该模板又会创建文档、视图和框架窗口。 有关此过程的说明，请参阅[文档模板创建](../mfc/document-template-creation.md)。

- 从 .ini 文件或 Windows 注册表加载标准文件选项，包括最近使用的文件的名称。

- 注册一个或多个文档模板。

- 对于 MDI 应用程序，创建主框架窗口。

- 处理命令行以打开命令行上指定的文档或打开新的空文档。

你可以添加自己的初始化代码或修改向导编写的代码。

> [!NOTE]
> MFC 应用程序必须初始化为单线程单元 （STA）。 如果在`InitInstance`重写中调用[Co初始化Ex，](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex)请指定COINIT_APARTMENTTHREADED（而不是COINIT_MULTITHREADED）。

## <a name="see-also"></a>另请参阅

[CWinApp：应用程序类](../mfc/cwinapp-the-application-class.md)
