---
title: 以编程方式打印
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC], active documents
- active documents [MFC], printing
- printing [MFC], programmatic
- IPrint interface
- printing [MFC]
ms.assetid: 3db0945b-5e13-4be4-86a0-6aecdae565bd
ms.openlocfilehash: eb8804610832f91f4b24487fddfe9c24a3799117
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342098"
---
# <a name="programmatic-printing"></a>以编程方式打印

OLE 提供了用于唯一标识永久文档 (`GetClassFile`) 并将其加载到其相关代码 (`CoCreateInstance`， `QueryInterface(IID_IPersistFile)`， `QueryInterface(IID_IPersistStorage)`， `IPersistFile::Load`，并`IPersistStorage::Load`)。 为了进一步启用打印文档，活动文档包容（使用最初未随 OLE 2.0 一起提供的现有 OLE 设计）引入了一个基本标准的打印接口 `IPrint`（通常可以通过任何能够加载文档类型的持久状态的对象获取）。 活动文档的每个视图都可以选择支持`IPrint`接口，以提供这些功能。

`IPrint` 接口定义如下：

```
interface IPrint : IUnknown
    {
    HRESULT SetInitialPageNum([in] LONG nFirstPage);
    HRESULT GetPageInfo(
        [out] LONG *pnFirstPage,
        [out] LONG *pcPages);
    HRESULT Print(
        [in] DWORD grfFlags,
        [in,out] DVTARGETDEVICE **pptd,
        [in,out] PAGESET ** ppPageSet,
        [in,out] STGMEDIUM **ppstgmOptions,
        [in] IContinueCallback* pCallback,
        [in] LONG nFirstPage,
        [out] LONG *pcPagesPrinted,
        [out] LONG *pnPageLast);
    };
```

客户端和容器只需使用`IPrint::Print`以指示要加载该文档时，指定打印控制标志、 目标设备、 要打印的页面后的文档和其他选项。 客户端还可以通过 `IContinueCallback` 接口来控制打印的继续（如下所示）。

此外，`IPrint::SetInitialPageNum`支持按一个编号页面无缝，显然对于类似 Office 活页夹的活动文档容器权益打印一系列文档的功能。 `IPrint::GetPageInfo` 使显示简单的分页信息通过允许调用方要检索的起始页之前传递给`SetInitialPageNum`（或文档的内部默认起始页码） 和文档中的页面数。

支持 `IPrint` 的对象在注册表中使用存储在该对象的 CLSID 下的“Printable”注册表项标记：

HKEY_CLASSES_ROOT\CLSID\\{...}\Printable

通常在支持 `IPrint` 或 `IPersistFile` 的相同对象上实现 `IPersistStorage`。 调用方通过查看注册表中的“Printable”注册表项，可以了解到以编程方式打印某些类的持久状态的能力。 "目前，Printable"指示支持至少`IPrint`; 其他接口可能定义了在将来的将可用于通过`QueryInterface`其中`IPrint`只是表示基本支持级别。

在打印过程中，您可能希望启动打印的客户端或容器控制打印是否应继续。 例如，容器可以支持应尽快终止打印作业的“停止打印”命令。 若要支持此功能，可打印对象的客户端可以使用 `IContinueCallback` 接口实现一个小的通知接收器对象：

```
interface IContinueCallback : IUnknown
    {
    HRESULT FContinue(void);
    HRESULT FContinuePrinting(
        [in] LONG cPagesPrinted,
        [in] LONG nCurrentPage,
        [in] LPOLESTR pszPrintStatus);
    };
```

此接口旨在作为采用 Win32 API 中的各种继续过程的位置的泛型继续回调函数很有用 (如`AbortProc`打印和`EnumMetafileProc`图元文件枚举)。 因此，在各种耗时的过程中，此接口设计都非常有用。

在最一般情况下，`IContinueCallback::FContinue`任何漫长的过程通过定期调用函数。 接收器对象返回 S_OK 以继续操作和 S_FALSE 以尽快停止过程。

`FContinue`但是，不使用的上下文中`IPrint::Print`; 相反，打印将使用`IContinueCallback::FContinuePrint`。 所有打印对象应定期调用`FContinuePrinting`传递已经打印的页数、 将要打印的页的页码和一个附加的字符串，该字符串描述客户端可能会选择要显示给用户 （如"页的打印状态5 的 19 英寸)。

## <a name="see-also"></a>请参阅

[活动文档容器](../mfc/active-document-containers.md)
