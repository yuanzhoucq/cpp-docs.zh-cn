---
title: TN071:IOleCommandTarget 实现
ms.date: 06/28/2018
f1_keywords:
- IOleCommandTarget
helpviewer_keywords:
- TN071 [MFC]
- IOleCommandTarget interface [MFC]
ms.assetid: 3eef571e-6357-444d-adbb-6f734a0c3161
ms.openlocfilehash: dca1183a17fe8f3022f517d1ad0c3932ea272417
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167993"
---
# <a name="tn071-mfc-iolecommandtarget-implementation"></a>TN071:IOleCommandTarget 实现

> [!NOTE]
> 以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

`IOleCommandTarget`接口允许对象和其容器以分派到每个其他的命令。 例如，对象的工具栏可能包含命令的按钮如`Print`， `Print Preview`， `Save`， `New`，和`Zoom`。 如果在支持的容器中嵌入了此类对象`IOleCommandTarget`，该对象可能允许其按钮和转发到容器，以处理用户单击它们时的命令。 如果容器想要打印自身的嵌入的对象，它可以通过发送通过命令发出此请求`IOleCommandTarget`嵌入对象的接口。

`IOleCommandTarget` 客户端使用它调用的服务器上的方法是一个类似于自动化的接口。 但是，使用`IOleCommandTarget`将保存通过自动化接口进行调用，因为程序员无需使用高昂的开销`Invoke`方法的`IDispatch`。

在 MFC 中，`IOleCommandTarget`活动文档服务器使用接口以允许活动文档容器要调度到服务器的命令。 活动文档服务器类， `CDocObjectServerItem`，使用 MFC 接口映射 (请参阅[TN038:MFC/OLE IUnknown 实现](../mfc/tn038-mfc-ole-iunknown-implementation.md)) 来实现`IOleCommandTarget`接口。

`IOleCommandTarget` 此外实现在`COleFrameHook`类。 `COleFrameHook` 是一个未记录的 MFC 类，实现就地编辑容器的框架窗口功能。 `COleFrameHook` 此外使用 MFC 接口映射实现`IOleCommandTarget`接口。 `COleFrameHook`实现`IOleCommandTarget`OLE 将命令转发给`COleDocObjectItem`-派生的活动文档容器。 这样，任何 MFC 活动文档容器中包含的活动文档服务器接收消息。

## <a name="mfc-ole-command-maps"></a>MFC OLE 命令映射

MFC 开发人员可以充分利用`IOleCommandTarget`通过使用 MFC OLE 命令映射。 OLE 命令映射为像消息映射，因为它们可以用于将 OLE 命令映射到包含该命令映射的类的成员函数。 若要完成此操作，请将置于命令映射来指定想要处理的命令、 OLE 命令和命令 ID 的 OLE 命令组宏[WM_COMMAND](/windows/desktop/menurc/wm-command)时收到 OLE 命令时，将发送的消息。 MFC 还提供了大量预定义的宏，标准 OLE 命令。 一组标准 OLE 命令的最初设计为与 Microsoft Office 应用程序使用，请参阅 OLECMDID 枚举 docobj.h 中定义。

当包含 OLE 命令映射的 MFC 应用程序收到 OLE 命令时，MFC 将尝试查找应用程序的 OLE 命令映射中请求的命令的命令 ID 和命令组。 如果找到匹配项，则 WM_COMMAND 消息被调度到包含具有请求的命令 ID 的命令映射的应用程序。 (请参阅的说明`ON_OLECMD`下面。)这样一来，mfc OLE 命令调度到应用程序转变成 WM_COMMAND 消息。 WM_COMMAND 消息被路由到应用程序的消息映射使用 MFC 标准[命令传送](../mfc/command-routing.md)体系结构。

与不同的消息映射，MFC OLE 命令映射不受类向导。 MFC 开发人员必须手动添加 OLE 命令映射支持和 OLE 命令映射条目。 可以将地图添加到 WM_COMMAND 消息路由链中时为活动文档的任何类中的 MFC 活动文档服务器的 OLE 命令是在容器中的处于就地活动状态。 这些类包括应用程序的类派生自[CWinApp](../mfc/reference/cwinapp-class.md)， [CView](../mfc/reference/cview-class.md)， [CDocument](../mfc/reference/cdocument-class.md)，以及[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)。 在活动文档容器中，可以仅为 OLE 命令映射添加到[COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)-派生的类。 此外，在活动文档容器中 WM_COMMAND 消息将只被调度到的消息映射中`COleDocObjectItem`-派生的类。

## <a name="ole-command-map-macros"></a>OLE 命令映射宏

使用以下宏将命令映射功能添加到您的类：

```cpp
DECLARE_OLECMD_MAP ()
```

包含命令映射的类 （通常在标头文件中） 的类声明中将此宏。

```cpp
BEGIN_OLECMD_MAP(theClass, baseClass)
```

*theClass*<br/>
包含命令映射的类的名称。

*baseClass*<br/>
包含命令映射的类的基类的名称。

此宏表示命令映射的开头。 包含命令映射的类在实现文件中使用此宏。

```
END_OLECMD_MAP()
```

此宏会将命令映射的结尾标记。 包含命令映射的类在实现文件中使用此宏。 此宏必须始终遵循 BEGIN_OLECMD_MAP 宏。

```
ON_OLECMD(pguid, olecmdid, id)
```

*pguid*<br/>
指向 OLE 命令的命令组的 GUID。 此参数是**NULL**标准 OLE 命令组。

*olecmdid*<br/>
OLE 命令要调用的命令 ID。

*id*<br/>
WM_COMMAND 消息发送到调用此 OLE 命令时包含命令映射的应用程序的 ID。

使用命令映射中 ON_OLECMD 宏以添加你想要处理的 OLE 命令的条目。 收到的 OLE 命令，它们将转换为指定的 WM_COMMAND 消息并通过使用标准 MFC 命令路由体系结构的应用程序的消息映射路由。

## <a name="example"></a>示例

下面的示例演示如何将 OLE 命令处理功能添加到 MFC 活动文档服务器来处理[OLECMDID_PRINT](/windows/desktop/api/docobj/ne-docobj-olecmdid) OLE 命令。 此示例假定使用应用程序向导生成的 MFC 应用程序是活动文档服务器。

1. 在你`CView`的派生类的标头文件中，将 DECLARE_OLECMD_MAP 宏添加到类声明。

    > [!NOTE]
    > 使用`CView`-因为它是 WM_COMMAND 消息路由链中的活动文档服务器中的类之一派生的类。

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

2. 在实现文件的`CView`-派生的类，添加 BEGIN_OLECMD_MAP 和 END_OLECMD_MAP 宏：

    ```cpp
    BEGIN_OLECMD_MAP(CMyServerView, CView)

    END_OLECMD_MAP()
    ```

3. 若要处理标准 OLE 打印命令，添加[ON_OLECMD](reference/message-map-macros-mfc.md#on_olecmd)指定的 OLE 命令 ID 的标准打印命令的命令映射到宏和**ID_FILE_PRINT** WM_COMMAND id。 **ID_FILE_PRINT**是应用程序向导生成 MFC 应用程序使用打印命令 ID 的标准：

    ```
    BEGIN_OLECMD_MAP(CMyServerView, CView)
        ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)
    END_OLECMD_MAP()
    ```

请注意，因为其中一个标准的 OLE 命令宏中 afxdocob.h，, 定义可能 ON_OLECMD 宏代替使用**OLECMDID_PRINT**是标准的 OLE 命令 id。 ON_OLECMD_PRINT 宏将完成与 ON_OLECMD 宏如上所示相同的任务。

容器应用程序时将此服务器发送**OLECMDID_PRINT**通过服务器的命令`IOleCommandTarget`接口，MFC 打印命令处理程序将调用服务器，从而导致服务器打印应用程序中。 活动文档容器的代码以调用在上述步骤中添加打印命令将如下所示：

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

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
