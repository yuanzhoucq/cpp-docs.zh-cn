---
title: TN016： 对使用C++使用 MFC 的多个继承
ms.date: 06/28/2018
f1_keywords:
- vc.inheritance
helpviewer_keywords:
- TN016
- MI (Multiple Inheritance)
- multiple inheritance, MFC support for
ms.assetid: 4ee27ae1-1410-43a5-b111-b6af9b84535d
ms.openlocfilehash: 76dc2e856ca7db783ee542aa2dbb498fd4c1a769
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306124"
---
# <a name="tn016-using-c-multiple-inheritance-with-mfc"></a>TN016： 对使用C++使用 MFC 的多个继承

本说明介绍如何将多重继承 (MI) 与 Microsoft 基础类一起使用。 MI 不一定要与 MFC 一起使用。 MI 不在任何 MFC 类中使用，并且不需要编写类库。

以下子主题说明了 MI 对常见 MFC 用语的影响，并介绍了 MI 的一些限制。 其中的一些限制是一般 C++ 限制。 其他限制是 MFC 体系结构带来的。

在本技术说明的结尾，您将发现使用 MI 的完整 MFC 应用程序。

## <a name="cruntimeclass"></a>CRuntimeClass

持久性和 MFC 使用的动态对象创建机制[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)数据结构唯地标识类。 MFC 将这些结构之一与应用程序中的每个动态和/或可序列化类关联。 这些结构通过 `AFX_CLASSINIT` 类型的特殊静态对象之一在应用程序启动时初始化。

`CRuntimeClass` 的当前实现不支持 MI 运行时类型信息。 这并不意味着您在不能在 MFC 应用程序中使用 MI。 但是，当您使用具有多个基类的对象时，您将负有某些责任。

[CObject::IsKindOf](../mfc/reference/cobject-class.md#iskindof)方法将不正确确定对象类型具有多个基类。 因此，不能使用[CObject](../mfc/reference/cobject-class.md)为虚拟基类，并为所有调用`CObject`之类的成员函数[cobject:: Serialize](../mfc/reference/cobject-class.md#serialize)和[CObject::operator 新](../mfc/reference/cobject-class.md#operator_new)必须具有范围限定符，以便C++可以消除相应函数调用。 当程序在 MFC 中使用 MI 时，包含 `CObject` 基类的类需要是基类列表中最左侧的类。

替代方法是使用 `dynamic_cast` 运算符。 如果将具有 MI 的对象强制转换为其基类之一，则会强制编译器使用指定基类中的函数。 有关详细信息，请参阅[dynamic_cast 运算符](../cpp/dynamic-cast-operator.md)。

## <a name="cobject---the-root-of-all-classes"></a>CObject - 所有类的根

所有重要类都直接或间接从 `CObject` 类派生。 `CObject` 没有任何成员数据，但它确实有一些默认功能。 当您使用 MI 时，您通常从两个或多个 `CObject` 派生类进行继承。 下面的示例演示了一个类可以继承[CFrameWnd](../mfc/reference/cframewnd-class.md)和一个[CObList](../mfc/reference/coblist-class.md):

```cpp
class CListWnd : public CFrameWnd, public CObList
{
    // ...
};
CListWnd myListWnd;
```

在这种情况下，`CObject` 将被包含两次。 这意味着您需要一种消除对 `CObject` 方法或运算符的任何引用的多义性的方法。 **运算符 new**并[运算符 delete](../mfc/reference/cobject-class.md#operator_delete)都必须消除歧义的两个运算符。 另举一例，以下代码导致在编译时出现错误：

```cpp
myListWnd.Dump(afxDump); // compile time error, CFrameWnd::Dump or CObList::Dump
```

## <a name="reimplementing-cobject-methods"></a>Reimplementing CObject 方法

当您要创建包含两个或更多 `CObject` 派生基类的新类时，应重新实现您希望其他人使用的 `CObject` 方法。 运算符**新**并**删除**都是必需的并且[转储](../mfc/reference/cobject-class.md#dump)建议。 以下示例重新实现**新**并**删除**运算符和`Dump`方法：

```cpp
class CListWnd : public CFrameWnd, public CObList
{
public:
    void* operator new(size_t nSize)
    {
        return CFrameWnd:: operator new(nSize);
    }
    void operator delete(void* p)
    {
        CFrameWnd:: operator delete(p);
    }
    void Dump(CDumpContent& dc)
    {
        CFrameWnd::Dump(dc);
        CObList::Dump(dc);
    }
    // ...
};
```

## <a name="virtual-inheritance-of-cobject"></a>CObject 的虚拟继承

以虚拟方式继承 `CObject` 看起来似乎能解决函数多义性问题，但事实并非如此。 由于 `CObject` 中没有成员数据，您不需要虚拟继承来防止多次复制基类成员数据。 在前面所示的第一个示例中，`Dump` 虚方法仍不明确，因为它在 `CFrameWnd` 和 `CObList`中的实现方式不同。 消除多义性的最佳方法是遵循上一节中提供的建议。

## <a name="cobjectiskindof-and-run-time-typing"></a>CObject::IsKindOf 和运行时类型检查

中受 MFC 支持运行时类型检查机制`CObject`使用 DECLARE_DYNAMIC、 IMPLEMENT_DYNAMIC、 DECLARE_DYNCREATE、 IMPLEMENT_DYNCREATE、 DECLARE_SERIAL 和 IMPLEMENT_SERIAL 宏。 这些宏可执行运行时类型检查以保证向下转换的安全性。

这些宏仅支持一个基类，并且以有限的方式用于多重继承类。 IMPLEMENT_DYNAMIC 或 IMPLEMENT_SERIAL 中指定的基类应是第一个 （或最左侧的） 基类。 此位置将使您能够仅为最左侧的基类执行类型检查。 运行时类型系统将对附加基类一无所知。 在以下示例中，运行时系统将对 `CFrameWnd` 执行类型检查，但对 `CObList` 一无所知。

```cpp
class CListWnd : public CFrameWnd, public CObList
{
    DECLARE_DYNAMIC(CListWnd)
    // ...
};
IMPLEMENT_DYNAMIC(CListWnd, CFrameWnd)
```

## <a name="cwnd-and-message-maps"></a>CWnd 和消息映射

若要使 MFC 消息映射系统正常工作，需满足两个附加要求：

- 只能有一个 `CWnd` 派生基类。

- `CWnd` 派生基类必须是第一个（或最左侧的）基类。

下面是该系统无法正常工作的一些示例：

```cpp
class CTwoWindows : public CFrameWnd, public CEdit
{ /* ... */ }; // error : two copies of CWnd

class CListEdit : public CObList, public CEdit
{ /* ... */ }; // error : CEdit (derived from CWnd) must be first
```

## <a name="a-sample-program-using-mi"></a>使用 MI 的示例程序

下面的示例是一个独立的应用程序组成的一个类派生自`CFrameWnd`并[CWinApp](../mfc/reference/cwinapp-class.md)。 我们不建议以这种方式构建应用程序，但这是包含一个类的最小的 MFC 应用程序的示例。

```cpp
#include <afxwin.h>

class CHelloAppAndFrame : public CFrameWnd, public CWinApp
{
public:
    CHelloAppAndFrame() {}

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

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
