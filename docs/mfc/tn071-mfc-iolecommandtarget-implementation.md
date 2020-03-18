---
title: TN071：MFC IOleCommandTarget 实现
ms.date: 06/28/2018
helpviewer_keywords:
- TN071 [MFC]
- IOleCommandTarget interface [MFC]
ms.assetid: 3eef571e-6357-444d-adbb-6f734a0c3161
ms.openlocfilehash: 56745e7985c8af97b0b628d148586ccef346d95a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442070"
---
# <a name="tn071-mfc-iolecommandtarget-implementation"></a>TN071：MFC IOleCommandTarget 实现

> [!NOTE]
> 以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

`IOleCommandTarget` 接口使对象及其容器能够彼此之间发送命令。 例如，对象的工具栏可能包含 `Print`、`Print Preview`、`Save`、`New`和 `Zoom`等命令的按钮。 如果此类对象嵌入支持 `IOleCommandTarget`的容器中，则对象可以启用其按钮，并将命令转发到容器，以便在用户单击它们时进行处理。 如果容器希望嵌入对象自行打印，则可以通过使用嵌入对象的 `IOleCommandTarget` 接口发送命令来发出此请求。

`IOleCommandTarget` 是一种自动化的接口，因为客户端使用它来调用服务器上的方法。 但是，使用 `IOleCommandTarget` 会节省通过自动化接口进行调用的开销，因为程序员不必使用通常昂贵的 `Invoke` `IDispatch`方法。

在 MFC 中，活动文档服务器使用 `IOleCommandTarget` 接口，以允许活动文档容器将命令分派给服务器。 活动文档服务器类 `CDocObjectServerItem`使用 MFC 接口映射（请参阅[TN038： mfc/OLE IUnknown 实现](../mfc/tn038-mfc-ole-iunknown-implementation.md)）来实现 `IOleCommandTarget` 接口。

`IOleCommandTarget` 也是在 `COleFrameHook` 类中实现的。 `COleFrameHook` 是一种未记录的 MFC 类，用于实现就地编辑容器的框架窗口功能。 `COleFrameHook` 还使用 MFC 接口映射实现 `IOleCommandTarget` 接口。 `COleFrameHook`的实现 `IOleCommandTarget` 将 OLE 命令转发到 `COleDocObjectItem`派生的活动文档容器。 这允许任何 MFC 活动文档容器从包含的活动文档服务器接收消息。

## <a name="mfc-ole-command-maps"></a>MFC OLE 命令映射

MFC 开发人员可以使用 MFC OLE 命令映射来利用 `IOleCommandTarget`。 OLE 命令映射类似于消息映射，因为它们可用于将 OLE 命令映射到包含命令映射的类的成员函数。 若要完成此操作，请在命令映射中放置宏，以指定要处理的命令的 OLE 命令组、OLE 命令以及接收 OLE 命令时将发送的[WM_COMMAND](/windows/win32/menurc/wm-command)消息的命令 ID。 MFC 还为标准 OLE 命令提供了许多预定义的宏。 有关最初设计用于 Microsoft Office 应用程序的标准 OLE 命令的列表，请参阅 docobj 中定义的 OLECMDID 枚举。

当包含 OLE 命令映射的 MFC 应用程序收到 OLE 命令时，MFC 会尝试在应用程序的 OLE 命令映射中查找请求的命令的命令 ID 和命令组。 如果找到匹配项，则会将 WM_COMMAND 消息分派给包含命令映射的应用程序，该应用程序包含请求的命令的 ID。 （请参阅下面 `ON_OLECMD` 的说明。）通过这种方式，按 MFC 将已调度到应用程序的 OLE 命令转换为 WM_COMMAND 消息。 然后，使用 MFC 标准[命令路由](../mfc/command-routing.md)体系结构通过应用程序的消息映射来路由 WM_COMMAND 消息。

与消息映射不同，ClassWizard 不支持 MFC OLE 命令映射。 MFC 开发人员必须手动添加 OLE 命令映射支持和 OLE 命令映射项。 如果活动文档在容器中处于活动状态，则可以将 OLE 命令映射添加到 WM_COMMAND 消息路由链中的任何类中的 MFC 活动文档服务器。 这些类包括从[CWinApp](../mfc/reference/cwinapp-class.md)、 [CView](../mfc/reference/cview-class.md)、 [CDocument](../mfc/reference/cdocument-class.md)和[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)派生的应用程序类。 在活动文档容器中，只能将 OLE 命令映射添加到[COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)派生类。 此外，在活动文档容器中，只会将 WM_COMMAND 消息调度到 `COleDocObjectItem`派生类中的消息映射。

## <a name="ole-command-map-macros"></a>OLE 命令映射宏

使用以下宏将命令映射功能添加到你的类：

```cpp
DECLARE_OLECMD_MAP ()
```

此宏将进入包含命令映射的类的类声明（通常在头文件中）。

```cpp
BEGIN_OLECMD_MAP(theClass, baseClass)
```

*类*<br/>
包含命令映射的类的名称。

*baseClass*<br/>
包含命令映射的类的基类的名称。

此宏标记命令映射的开头。 在包含命令映射的类的实现文件中使用此宏。

```
END_OLECMD_MAP()
```

此宏标记命令映射的结尾。 在包含命令映射的类的实现文件中使用此宏。 此宏必须始终跟在 BEGIN_OLECMD_MAP 宏之后。

```
ON_OLECMD(pguid, olecmdid, id)
```

*pguid*<br/>
指向 OLE 命令的命令组的 GUID 的指针。 对于标准 OLE 命令组，此参数为**NULL** 。

*olecmdid*<br/>
要调用的命令的 OLE 命令 ID。

*id*<br/>
调用此 OLE 命令时要发送到包含命令映射的应用程序的 WM_COMMAND 消息的 ID。

使用命令映射中的 ON_OLECMD 宏为要处理的 OLE 命令添加条目。 接收到 OLE 命令后，它们将被转换为指定的 WM_COMMAND 消息，并使用标准 MFC 命令路由体系结构通过应用程序的消息映射进行路由。

## <a name="example"></a>示例

下面的示例演示如何将 OLE 命令处理功能添加到 MFC 活动文档服务器来处理[OLECMDID_PRINT](/windows/win32/api/docobj/ne-docobj-olecmdid) OLE 命令。 此示例假设你使用了应用程序向导生成作为活动文档服务器的 MFC 应用程序。

1. 在 `CView`派生类的标头文件中，将 DECLARE_OLECMD_MAP 宏添加到类声明中。

    > [!NOTE]
    > 使用派生 `CView`的类，因为它是位于 WM_COMMAND 消息路由链中的活动文档服务器中的一个类。

    ```cpp
    class CMyServerView : public CView
    {
    protected: // create from serialization only
        CMyServerView();
        DECLARE_DYNCREATE(CMyServerView)
        DECLARE_OLECMD_MAP()
        // . . .
    };
    ```

2. 在 `CView`派生类的实现文件中，添加 BEGIN_OLECMD_MAP 和 END_OLECMD_MAP 宏：

    ```cpp
    BEGIN_OLECMD_MAP(CMyServerView, CView)

    END_OLECMD_MAP()
    ```

3. 若要处理标准 OLE 打印命令，请将[ON_OLECMD](reference/message-map-macros-mfc.md#on_olecmd)宏添加到命令映射中，为标准打印命令指定 OLE 命令 ID，并为 WM_COMMAND ID **ID_FILE_PRINT** 。 **ID_FILE_PRINT**是由应用程序生成的 MFC 应用程序使用的标准打印命令 ID：

    ```
    BEGIN_OLECMD_MAP(CMyServerView, CView)
        ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)
    END_OLECMD_MAP()
    ```

请注意，在 afxdocob 中定义的一个标准 OLE 命令宏可用于代替 ON_OLECMD 宏，因为**OLECMDID_PRINT**是标准的 OLE 命令 ID。 ON_OLECMD_PRINT 宏将完成与上面所示的 ON_OLECMD 宏相同的任务。

当容器应用程序通过服务器的 `IOleCommandTarget` 接口向此服务器发送**OLECMDID_PRINT**命令时，将在服务器中调用 MFC 打印命令处理程序，从而使服务器打印应用程序。 用于调用上述步骤中添加的打印命令的活动文档容器的代码如下所示：

```cpp
void CContainerCntrItem::DoOleCmd()
{
    IOleCommandTarget *pCmd = NULL;
    HRESULT hr = E_FAIL;
    OLECMD ocm={OLECMDID_PRINT, 0};

    hr = m_lpObject->QueryInterface(
        IID_IOleCommandTarget,reinterpret_cast<void**>(&pCmd));

    if (FAILED(hr))
        return;

    hr = pCmd->QueryStatus(NULL, 1, &ocm, NULL);

    if (SUCCEEDED(hr) && (ocm.cmdf& OLECMDF_ENABLED))
    {
        //Command is available and enabled so call it
        COleVariant vIn;
        COleVariant vOut;
        hr = pCmd->Exec(NULL, OLECMDID_PRINT,
            OLECMDEXECOPT_DODEFAULT, &vIn, &vOut);
        ASSERT(SUCCEEDED(hr));
    }
    pCmd->Release();
}
```

## <a name="see-also"></a>另请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
