---
title: "TN071：MFC IOleCommandTarget 实现 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IOleCommandTarget"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IOleCommandTarget 接口"
  - "TN071"
ms.assetid: 3eef571e-6357-444d-adbb-6f734a0c3161
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN071：MFC IOleCommandTarget 实现
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。  因此，某些过程和主题可能已过时或不正确。  要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 `IOleCommandTarget` 接口启用对象，它们为计划彼此命令的容器。  例如，对象可能包含的工具栏命令的按钮 \(如 **打印**、**打印预览**、**保存**、**缩放**和 `New`。  如果此对象支持在 `IOleCommandTarget`容器的嵌入，对象无法启用其按钮和前进到处理命令的用户何时单击这些容器。  如果容器中嵌入对象打印，则可以通过命令发送使此请求通过嵌入对象的 `IOleCommandTarget` 接口。  
  
 `IOleCommandTarget` 是一个自动化的接口。由于客户用于它调用服务器的方法。  但是，程序员不必使用 `IDispatch`，通常成本较大的 `Invoke` 方法使用 `IOleCommandTarget` 通过自动化接口将系统调用。  
  
 在 MFC 中，对活动文档服务器用于 `IOleCommandTarget` 接口允许活动文档容器和命令到服务器。  活动文档服务器类，`CDocObjectServerItem`，使用 MFC 接口映射 \(参见 [TN038:MFC\/OLE IUnknown 实现](../mfc/tn038-mfc-ole-iunknown-implementation.md)\) 实现 `IOleCommandTarget` 接口。  
  
 `IOleCommandTarget` 位于 **COleFrameHook** 类还实现。  **COleFrameHook** 是实现就地编辑容器的框架窗口功能的使用未证明的 MFC 类。  **COleFrameHook** 还使用 MFC 接口映射实现 `IOleCommandTarget` 接口。  `IOleCommandTarget` 的**COleFrameHook** 实现寄 OLE 命令到 `COleDocObjectItem`派生的活动文档容器。  这允许所有 MFC 活动文档容器从包含的活动文档服务器的消息。  
  
## MFC OLE 命令映射  
 使用 MFC 的 OLE 命令映射 MFC，开发人员可以使用 `IOleCommandTarget`。  OLE 命令映射与消息映射，因为它们可用于映射 OLE 命令命令映射到包含类的成员函数。  进行此工作、将在宏命令映射指定要处理命令的 OLE 命令组，OLE 命令和路由命令 ID [WM\_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) OLE 命令信息，当收到。  MFC 提供标准 OLE 命令还提供了许多预定义宏。  有关最初设计用于 Microsoft Office 应用程序使用标准 OLE 命令的列表，请参见 OLECMDID 枚举，在 docobj.h 定义。  
  
 将 OLE 命令均由包含一个 OLE 命令映射的 MFC 应用程序时收到，MFC 尝试找到命令 ID 和命令组命令请求在应用程序中。的 OLE 命令映射。  如果找到匹配，**WM\_COMMAND** 消息调度对包含请求命令的 ID 将应用程序命令映射。\(请参见下面的 `ON_OLECMD` 说明。\)因此，OLE 命令调度对应用程序变为 **WM\_COMMAND** 消息由 MFC。  标准 MFC 使用 [命令传送](../mfc/command-routing.md) 结构，**WM\_COMMAND** 消息通过应用程序的消息映射然后路由。  
  
 与不同消息映射，MFC OLE 命令映射 ClassWizard 不受支持。  MFC 开发人员必须手动添加 OLE 命令映射支持和 OLE 命令映射项。  OLE 命令映射可添加到 MFC 在 **WM\_COMMAND** 消息路由链在活动文档处于就地活动容器中的任何类的活动文档服务器。  这些类包括应用程序的类从派生，[CView](../mfc/reference/cview-class.md)[CDocument](../mfc/reference/cdocument-class.md)[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)[CWinApp](../mfc/reference/cwinapp-class.md)、和。  在活动文档容器，OLE 命令映射只能添加到 [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)派生类。  此外，在活动文档容器，**WM\_COMMAND** 消息将仅调度到 `COleDocObjectItem`消息映射的派生类。  
  
## OLE 命令映射宏  
 使用以下宏将命令添加映射函数添加到类：  
  
```  
  
DECLARE_OLECMD_MAP ()  
  
```  
  
 该宏在类声明中 \(通常在头文件包含命令映射\) 的类。  
  
```  
  
BEGIN_OLECMD_MAP(  
theClass  
,   
baseClass  
)  
  
```  
  
 `theClass`  
 包含命令映射的类的名称。  
  
 `baseClass`  
 类的基类的名称包含命令映射。  
  
 此宏命令指示映射的开头。  使用此宏实现文件中包含的命令映射的类。  
  
```  
  
END_OLECMD_MAP()  
  
```  
  
 此宏命令指示映射的结尾。  使用此宏实现文件中包含的命令映射的类。  此宏必须始终遵循 **BEGIN\_OLECMD\_MAP** 宏。  
  
```  
  
ON_OLECMD(  
pguid  
,   
olecmdid  
,   
id  
)  
  
```  
  
 `pguid`  
 \[out\] 指向命令命令组 GUID 的OLE指针。  此参数是标准 OLE 命令组的 **NULL**。  
  
 *olecmdid*  
 命令的 OLE 命令 ID 调用。  
  
 `id`  
 要发送的消息映射到 **WM\_COMMAND** 的 ID 包含命令的应用程序，当该 OLE 命令调用。  
  
 使用 `ON_OLECMD` 宏。命令添加映射要处理的 OLE 命令的输入。  当 OLE 命令接收，使用标准 MFC 命令传送结构，其将转换为指定的 **WM\_COMMAND** 消息并通过应用程序的消息映射路由。  
  
## 示例  
 下面的示例显示如何添加 OLE 命令处理功能向 MFC 活动文档服务器处理 [OLECMDID\_PRINT](http://msdn.microsoft.com/library/windows/desktop/ms691264) OLE 命令。  此示例假定中，使用 AppWizard 生成是活动文档服务器的 MFC 应用程序。  
  
1.  在 `CView`派生类的头文件，添加 `DECLARE_OLECMD_MAP` 宏。类声明。  
  
    > [!NOTE]
    >  请使用 `CView`派生类，因为它是一在 **WM\_COMMAND** 消息路由字符串的活动文档服务器的类。  
  
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
  
2.  在 `CView`的实现文件派生类，添加 `BEGIN_OLECMD_MAP` 和 `END_OLECMD_MAP` 宏：  
  
    ```  
    BEGIN_OLECMD_MAP(CMyServerView, CView)  
  
    END_OLECMD_MAP()  
    ```  
  
3.  若要处理标准 OLE 命令，请打印将 [ON\_OLECMD](../Topic/ON_OLECMD.md) 宏。指定 OLE 命令 ID 用于标准的打印和 **ID\_FILE\_PRINT** 命令的命令 **WM\_COMMAND** 映射为 ID.  **ID\_FILE\_PRINT** 是 AppWizard 生成的 MFC 应用程序使用打印的标准命令 ID:  
  
    ```  
    BEGIN_OLECMD_MAP(CMyServerView, CView)  
       ON_OLECMD(NULL,OLECMDID_PRINT,ID_FILE_PRINT)  
    END_OLECMD_MAP()  
    ```  
  
 这是因为 **OLECMDID\_PRINT** 是标准 OLE 命令 ID.，请注意，的标准 OLE 命令宏，在定义 afxdocob.h，可以在 `ON_OLECMD` 的位置使用宏  `ON_OLECMD_PRINT` 宏将完成任务和显示的宏相同 `ON_OLECMD` 上面。  
  
 在容器应用程序通过服务器的 `IOleCommandTarget` 接口发送此服务器 **OLECMDID\_PRINT** 命令，命令处理打印程序的 MFC 服务器中将调用，这会导致服务器应用程序打印。  打印"命令调用的活动文档容器的代码添加到上述步骤相仿：  
  
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
   if(SUCCEEDED(hr) && (ocm.cmdf & OLECMDF_ENABLED))  
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
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)