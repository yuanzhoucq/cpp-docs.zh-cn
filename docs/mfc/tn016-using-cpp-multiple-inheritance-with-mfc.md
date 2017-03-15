---
title: "TN016：对 MFC 使用 C++ 多重继承 | Microsoft Docs"
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
  - "vc.inheritance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MI（多重继承）"
  - "多重继承, MFC 支持"
  - "TN016"
ms.assetid: 4ee27ae1-1410-43a5-b111-b6af9b84535d
caps.latest.revision: 22
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN016：对 MFC 使用 C++ 多重继承
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此注释说明如何使用 Microsoft 基础类的多继承 \(MI\)。  使用 MI 不需要与 MFC。  MI 不在任何 MFC 类且不需要编写类库。  
  
 下面的副主题介绍如何 MI 影响使用常见的 MFC MI 思路以及包括特定的限制。  其中的一些限制是一般 C\+\+ 限制。  MFC 应用其他体系结构。  
  
 在此技术声明结尾时将会使用 MI 的完整 MFC 应用程序。  
  
## CRuntimeClass  
 MFC 持久性和动态对象创建机制使用 [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) 数据结构唯一标识类。  MFC 将这些结构之一与应用程序中的每个动态和\/或序列化类。  这些结构初始化应用程序启动时，使用一个 `AFX_CLASSINIT`类型的静态对象。  
  
 `CRuntimeClass` 的当前实现不支持 MI 运行时类型信息。  这并不意味着您在 MFC 应用程序不能使用 MI。  但是，您将具有特定职责，当您使用具有多个基类的对象。  
  
 方法 [CObject::IsKindOf](../Topic/CObject::IsKindOf.md) 不准确确定对象的类型是否具有多个基类。  因此，不可以使用 [CObject](../mfc/reference/cobject-class.md) 作为虚拟基类，并将 `CObject` 成员函数，例如 [CObject::Serialize](../Topic/CObject::Serialize.md) 和 [CObject::operator new](../Topic/CObject::operator%20new.md) 的任何调用都必须有范围限定符，以便消除 C\+\+ 中适当的函数调用。  当程序使用在 MFC 中的 MI，包含 `CObject` 基类的类是在基类列表的最左端的类。  
  
 替代方法是使用`dynamic_cast`运算符。  转换为 MI 的对象到其基类之一。所提供的基类强制编译器将使用函数。  有关详细信息，请参阅[dynamic\_cast 运算符](../cpp/dynamic-cast-operator.md)。  
  
## CObject \- 所有类的根  
 所有重要的类从 `CObject`类直接或间接派生。  `CObject` 没有任何成员数据，但是，它具有一些默认功能。  当您使用 MI，则来自两个或多个 `CObject`派生的类通常继承。  下面的示例阐释如何从类继承：和 [CObList](../mfc/reference/coblist-class.md)[CFrameWnd](../mfc/reference/cframewnd-class.md)  
  
```  
class CListWnd : public CFrameWnd, public CObList  
{  
 ...  
};  
CListWnd myListWnd;  
```  
  
 在这种情况下会包括 `CObject` 的两倍。  这意味着您需要一种方式区分对 `CObject` 方法或运算符的所有引用。  `operator new`、[删除运算符](../Topic/CObject::operator%20delete.md) 是必须包含它的两个运算符。  另举一例，下面的代码将产生错误在编译时：  
  
```  
myListWnd.Dump(afxDump);  
    // compile time error, CFrameWnd::Dump or CObList::Dump ?  
```  
  
## Reimplementing CObject 方法  
 如果您要创建包含两个或更多个 `CObject` 派生的基类的类时，应重新实现 `CObject` 方法时希望其他人使用。  运算符 `new` 和 `delete` 是必须的，并建议 [转储](../Topic/CObject::Dump.md)。  下面的示例 reimplements `new` 和 `delete` 运算符和 `Dump` 方法：  
  
```  
class CListWnd : public CFrameWnd, public CObList  
{  
public:  
    void* operator new(size_t nSize)  
        { return CFrameWnd::operator new(nSize); }  
    void operator delete(void* p)  
        { CFrameWnd::operator delete(p); }  
  
    void Dump(CDumpContent& dc)  
        { CFrameWnd::Dump(dc);  
          CObList::Dump(dc); }  
     ...  
};  
```  
  
## CObject 虚拟继承  
 似乎虚拟继承 `CObject` 将函数解决多义性问题，但事实并非如此。  因为不在 `CObject`的数据成员，则不需要的虚拟继承防止基类成员数据的多个副本。  在前面显示的第一个示例中，`Dump` 虚方法不明确，因为在 `CFrameWnd` 和 `CObList`不同的方式实现。  最佳方式取消多义性将按照前面的部分提供的建议。  
  
## CObject::IsKindOf 和 Run\-Time Typing  
 在 `CObject` 的 MFC 支持的运行时间类型的机制使用宏 `DECLARE_DYNAMIC`、`IMPLEMENT_DYNAMIC`、`DECLARE_DYNCREATE`、`IMPLEMENT_DYNCREATE`、`DECLARE_SERIAL` 和 `IMPLEMENT_SERIAL`。  这些宏可执行运行时类型检查为保证安全的向下转换。  
  
 这些宏仅支持一个基类，并使用了一个有限方式的多继承的类。  在 `IMPLEMENT_DYNAMIC` 指定的基类或 `IMPLEMENT_SERIAL` 应是第一个 \(或的最左边\) 的基类。  此位置将使您能够仅执行最左边的基类的类型检查。  运行时类型系统不知道任何关于附加的基类。  在下面示例中，则运行时系统不会执行任何类型检查，`CFrameWnd`，但知道 `CObList`。  
  
```  
class CListWnd : public CFrameWnd, public CObList  
{  
    DECLARE_DYNAMIC(CListWnd)  
    ...  
};  
IMPLEMENT_DYNAMIC(CListWnd, CFrameWnd)  
```  
  
## CWnd 和消息映射  
 为了使变换正确工作 MFC 的系统消息映射，则另外两个要求：  
  
-   只能有一个 `CWnd`派生的基类。  
  
-   `CWnd`\- 从此基类必须是将第一个 \(或表示最左边的基类\)。  
  
 这不起作用的一些示例：  
  
```  
class CTwoWindows : public CFrameWnd, public CEdit  
    { ... };  
        // error : two copies of CWnd  
  
class CListEdit : public CObList, public CEdit  
    { ... };  
        // error : CEdit (derived from CWnd) must be first  
```  
  
## 使用 MI 的示例程序  
 下面的示例包括从 `CFrameWnd`、[CWinApp](../mfc/reference/cwinapp-class.md)派生的类的独立应用程序。  我们不建议这样生成一个应用程序，但是，这具有一个类最小的 MFC 应用程序。  
  
```  
#include <afxwin.h>  
  
class CHelloAppAndFrame : public CFrameWnd, public CWinApp  
{   
public:  
    CHelloAppAndFrame()  
        { }  
  
    // Necessary because of MI disambiguity  
    void* operator new(size_t nSize)  
        { return CFrameWnd::operator new(nSize); }  
    void operator delete(void* p)  
        { CFrameWnd::operator delete(p); }  
  
    // Implementation  
    // CWinApp overrides  
    virtual BOOL InitInstance();  
    // CFrameWnd overrides  
    virtual void PostNcDestroy();  
    afx_msg void OnPaint();  
  
    DECLARE_MESSAGE_MAP()  
  
};  
  
BEGIN_MESSAGE_MAP(CHelloAppAndFrame, CFrameWnd)  
    ON_WM_PAINT()  
END_MESSAGE_MAP()  
  
// because the frame window is not allocated on the heap, we must  
// override PostNCDestroy not to delete the frame object  
void CHelloAppAndFrame::PostNcDestroy()  
{  
    // do nothing (do not call base class)  
}  
  
void CHelloAppAndFrame::OnPaint()  
{  
    CPaintDC dc(this);  
    CRect rect;  
    GetClientRect(rect);  
  
    CString s = "Hello, Windows!";  
    dc.SetTextAlign(TA_BASELINE | TA_CENTER);  
    dc.SetTextColor(::GetSysColor(COLOR_WINDOWTEXT));  
    dc.SetBkMode(TRANSPARENT);  
    dc.TextOut(rect.right / 2, rect.bottom / 2, s);  
}  
  
// Application initialization  
BOOL CHelloAppAndFrame::InitInstance()  
{  
    // first create the main frame  
    if (!CFrameWnd::Create(NULL, "Multiple Inheritance Sample",  
        WS_OVERLAPPEDWINDOW, rectDefault))  
        return FALSE;  
  
    // the application object is also a frame window  
    m_pMainWnd = this;            
    ShowWindow(m_nCmdShow);  
    return TRUE;  
}  
  
CHelloAppAndFrame theHelloAppAndFrame;  
```  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)