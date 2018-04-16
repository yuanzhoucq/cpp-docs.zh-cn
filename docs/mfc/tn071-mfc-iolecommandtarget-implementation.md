---
title: "TN071: MFC IOleCommandTarget 实现 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IOleCommandTarget
dev_langs:
- C++
helpviewer_keywords:
- TN071 [MFC]
- IOleCommandTarget interface [MFC]
ms.assetid: 3eef571e-6357-444d-adbb-6f734a0c3161
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 43f97774036c42fa0f681a65e0a335f944daf09c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="tn071-mfc-iolecommandtarget-implementation"></a>TN071：MFC IOleCommandTarget 实现
> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 `IOleCommandTarget`接口允许对象和调度到每个其他的命令及其容器。 例如，对象的工具栏可能包含的命令按钮如**打印**，**打印预览**，**保存**， `New`，和**缩放**. 如果此类对象已在支持的容器中嵌入`IOleCommandTarget`，对象可能允许其按钮和转发到处理用户单击它们时的容器的命令。 如果容器想要打印本身的嵌入的对象，它无法通过发送通过命令来发出此请求`IOleCommandTarget`嵌入对象的接口。  
  
 `IOleCommandTarget`客户端可用它来调用方法的服务器上是类似于自动化的接口。 但是，使用`IOleCommandTarget`将保存通过自动化接口进行调用，因为程序员无需使用通常耗费大量资源的开销`Invoke`方法`IDispatch`。  
  
 在 MFC 中，`IOleCommandTarget`活动文档服务器使用接口来允许活动文档容器来调度到服务器的命令。 活动文档服务器类， `CDocObjectServerItem`，使用 MFC 接口映射 (请参阅[TN038: MFC/OLE IUnknown 实现](../mfc/tn038-mfc-ole-iunknown-implementation.md)) 来实现`IOleCommandTarget`接口。  
  
 `IOleCommandTarget`此外实现在**COleFrameHook**类。 **COleFrameHook**实现就地框架窗口功能的未记录的 MFC 类编辑容器。 **COleFrameHook**还使用 MFC 接口映射实现`IOleCommandTarget`接口。 **COleFrameHook**的实现`IOleCommandTarget`OLE 将命令转发给`COleDocObjectItem`-派生活动文档容器。 这样，任何 MFC 活动文档容器，从包含活动文档服务器接收消息。  
  
## <a name="mfc-ole-command-maps"></a>MFC OLE 命令映射  
 MFC 开发人员可以利用`IOleCommandTarget`通过使用 MFC OLE 命令映射。 OLE 命令图是类的像消息映射，因为它们可以用于将 OLE 命令映射到包含命令之间的映射的成员函数。 若要完成此操作，请将宏置于命令之间的映射以指定你想要处理的命令、 OLE 命令中，和的命令 ID 的 OLE 命令组[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)收到 OLE 命令时，将发送的消息。 MFC 还提供了大量预定义的宏，对于标准 OLE 命令。 有关标准 OLE 的列表为最初设计的命令使用与 Microsoft Office 应用程序，请参阅 OLECMDID 枚举 docobj.h 中定义。  
  
 当收到 OLE 命令时的 MFC 应用程序包含 OLE 命令之间的映射时，MFC 将尝试查找应用程序的 OLE 命令映射中请求的命令的命令 ID 和命令组。 如果找到匹配项，则**WM_COMMAND**消息调度到包含请求的命令的 ID 与命令之间的映射的应用程序。 (请参阅说明`ON_OLECMD`下面。)这种方式，OLE 调度到应用程序的命令会转换为**WM_COMMAND** mfc 的消息。 **WM_COMMAND**消息则传送通过使用 MFC 标准的应用程序的消息映射[命令路由](../mfc/command-routing.md)体系结构。  
  
 与不同的消息映射，ClassWizard 不支持 MFC OLE 命令映射。 MFC 开发人员必须手动添加 OLE 命令映射支持和 OLE 命令映射条目。 OLE 命令映射可以添加到处于任何类中的 MFC 活动文档服务器**WM_COMMAND**邮件路由链在活动文档容器中的处于就地活动状态的时间。 这些类包括应用程序的类派生自[CWinApp](../mfc/reference/cwinapp-class.md)， [CView](../mfc/reference/cview-class.md)， [CDocument](../mfc/reference/cdocument-class.md)，和[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)。 在活动文档容器，可以仅将 OLE 命令映射添加到[COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)-派生类。 此外，在活动文档容器**WM_COMMAND**仅都将消息调度到的消息映射中`COleDocObjectItem`-派生类。  
  
## <a name="ole-command-map-macros"></a>OLE 命令映射宏  
 使用以下宏将命令映射功能添加到你的类：  
  
```  
 
DECLARE_OLECMD_MAP ()  
 
```  
  
 包含命令之间的映射的类 （通常在标头文件中） 的类声明中将此宏。  
  
```  
 
BEGIN_OLECMD_MAP(
theClass  ,   baseClass)  
 
```  
  
 `theClass`  
 包含命令映射的类名称。  
  
 `baseClass`  
 包含命令之间的映射的类的基类的名称。  
  
 此宏将标记命令之间的映射的开头。 包含命令之间的映射的类的实现文件中使用此宏。  
  
```  
 
END_OLECMD_MAP()  
 
```  
  
 此宏将标记命令之间的映射的末尾。 包含命令之间的映射的类的实现文件中使用此宏。 此宏必须始终遵循**BEGIN_OLECMD_MAP**宏。  
  
```  
 
ON_OLECMD(
pguid  ,   
olecmdid  ,
    id)  
 
```  
  
 `pguid`  
 指向 OLE 命令的命令组的 GUID 的指针。 此参数是**NULL**标准 OLE 命令组。  
  
 *olecmdid*  
 要调用的命令 OLE 命令 ID。  
  
 `id`  
 ID **WM_COMMAND**消息发送到调用此 OLE 命令时包含命令之间的映射的应用程序。  
  
 使用`ON_OLECMD`命令映射，若要添加的 OLE 项中的宏的命令你想要处理。 收到的 OLE 命令，这些值将转换为指定**WM_COMMAND**消息，然后通过使用标准 MFC 命令路由体系结构的应用程序的消息映射路由。  
  
## <a name="example"></a>示例  
 下面的示例演示如何将 OLE 命令处理功能添加到 MFC 活动文档服务器来处理[OLECMDID_PRINT](http://msdn.microsoft.com/library/windows/desktop/ms691264) OLE 命令。 此示例假定你使用应用程序向导生成的 MFC 应用程序是活动文档服务器。  
  
1.  在你`CView`-派生类的标头文件中，添加`DECLARE_OLECMD_MAP`向类声明的宏。  
  
    > [!NOTE]
    >  使用`CView`-因为它是在活动文档服务器中的类之一派生类**WM_COMMAND**邮件路由链。  
  
 ```  
    class CMyServerView : public CView  
 {  
    protected: // create from serialization only  
    CMyServerView();
DECLARE_DYNCREATE(CMyServerView)  
    DECLARE_OLECMD_MAP() 
 . . .  
 };  
 ```  
  
2.  在实现文件中为`CView`-派生类中，添加`BEGIN_OLECMD_MAP`和`END_OLECMD_MAP`宏：  
  
 ```  
    BEGIN_OLECMD_MAP(CMyServerView, CView)  
 
    END_OLECMD_MAP() 
 ```  
  
3.  若要处理的标准 OLE 打印命令，添加[ON_OLECMD](reference/message-map-macros-mfc.md#on_olecmd)命令之间的映射指定标准的打印命令的 OLE 命令 ID 的宏和**ID_FILE_PRINT**为**WM_COMMAND** Id。 **ID_FILE_PRINT**是打印命令 ID 由 AppWizard 生成 MFC 应用程序的标准：  
  
 ```  
    BEGIN_OLECMD_MAP(CMyServerView,
    CView)  
    ON_OLECMD(NULL,
    OLECMDID_PRINT,
    ID_FILE_PRINT) 
    END_OLECMD_MAP() 
 ```  
  
 注意，其中一个标准的 OLE 命令宏，定义在 afxdocob.h，无法使用代替了`ON_OLECMD`宏因为**OLECMDID_PRINT**就是标准的 OLE 命令 id。 `ON_OLECMD_PRINT`宏将完成相同的任务`ON_OLECMD`上面所示的宏。  
  
 容器应用程序时将此服务器发送**OLECMDID_PRINT**通过服务器的命令`IOleCommandTarget`接口，MFC 打印命令处理程序将调用在服务器中，从而导致打印应用程序服务器。 活动文档容器的代码以调用在上述步骤中添加打印命令将如下所示：  
  
```  
void CContainerCntrItem::DoOleCmd()  
{  
    IOleCommandTarget *pCmd = NULL;  
    HRESULT hr = E_FAIL;  
    OLECMD ocm={OLECMDID_PRINT, 0};  
 
    hr = m_lpObject->QueryInterface(IID_IOleCommandTarget,reinterpret_cast<void**>(&pCmd));

    if(FAILED(hr)) 
    return; 
 
    hr = pCmd->QueryStatus(NULL, 1, &ocm, NULL);

    if(SUCCEEDED(hr)&& (ocm.cmdf& OLECMDF_ENABLED))  
 { *//Command is available and enabled so call it  
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
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

