---
title: TN064:单元模型线程中的 ActiveX 控件
ms.date: 11/04/2016
f1_keywords:
- vc.controls.activex
helpviewer_keywords:
- OLE controls [MFC], container support
- containers [MFC], multithreaded
- TN064 [MFC]
- multithread container [MFC]
- apartment model threading [MFC]
ms.assetid: b2ab4c88-6954-48e2-9a74-01d4a60df073
ms.openlocfilehash: d6f02b2106693226f6380e935a54e04e10d5b4f8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351821"
---
# <a name="tn064-apartment-model-threading-in-activex-controls"></a>TN064:单元模型线程中的 ActiveX 控件

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

此技术说明介绍如何启用 ActiveX 控件中的单元模型线程。 请注意，单元模型线程处理仅支持在视觉对象中C++版本 4.2 或更高版本。

## <a name="what-is-apartment-model-threading"></a>什么是单元模型线程处理

单元模型是一种支持嵌入的对象，例如 ActiveX 控件，在多线程的容器应用程序中的方法。 尽管应用程序可能有多个线程，嵌入对象的每个实例将分配给一个"apartment，"这将在只有一个线程上执行。 换而言之，对控件的实例的所有调用将都发生在同一线程上。

但是，相同类型的控件的不同实例可能会分配到不同的单元。 因此，如果控件的多个实例共享常见 （例如，静态或全局数据） 中的任何数据，然后对此共享数据的访问需要保护的同步对象，如关键部分。

有关单元线程处理模型的完整详细信息，请参阅[进程和线程](/windows/desktop/ProcThread/processes-and-threads)中*OLE 程序员参考*。

## <a name="why-support-apartment-model-threading"></a>为什么支持单元模型线程

可在多线程的容器应用程序还支持单元模型的支持的单元模型线程的控件。 如果未启用的单元模型线程，将限制可以在其中使用您的控件的容器的潜在一组。

启用单元模型线程很容易对大多数控件，尤其是当它们具有很少或没有共享的数据。

## <a name="protecting-shared-data"></a>保护共享数据

如果您的控件使用共享的数据的静态成员变量，如访问数据应受到保护的关键部分，以防止多个线程同时修改的数据。 若要实现此目的设置临界区，请声明类的静态成员变量`CCriticalSection`中控件的类。 使用`Lock`和`Unlock`此临界区的成员函数对象，无论你的代码访问的共享的数据。

例如，考虑需要维护的所有实例都共享的字符串的控件类。 此字符串可在静态成员变量中维护和保护的关键部分。 控件的类声明将包含以下信息：

```
class CSampleCtrl : public COleControl
{
...
    static CString _strShared;
    static CCriticalSection _critSect;
};
```

类的实现将包含这些变量的定义：

```
int CString CSampleCtrl::_strShared;
CCriticalSection CSampleCtrl::_critSect;
```

访问`_strShared`静态成员然后受关键部分：

```
void CSampleCtrl::SomeMethod()
{
    _critSect.Lock();
if (_strShared.Empty())
    _strShared = "<text>";
    _critSect.Unlock();

...
}
```

## <a name="registering-an-apartment-model-aware-control"></a>注册一个可识别单元模型的控件

支持的单元模型线程的控件应在注册表中，此功能通过添加命名的值"ThreadingModel"指示的"Apartment"下其类 ID 注册表项中的值*类 id* \\ **InprocServer32**密钥。 若要使此密钥会自动注册为您的控件，请将传递*afxregapartmentthreading 改*中的第六个参数的标志`AfxOleRegisterControlClass`:

```
BOOL CSampleCtrl::CSampleCtrlFactory::UpdateRegistry(BOOL bRegister)
{
    if (bRegister)
    return AfxOleRegisterControlClass(
    AfxGetInstanceHandle(),
    m_clsid,
    m_lpszProgID,
    IDS_SAMPLE,
    IDB_SAMPLE,
    afxRegApartmentThreading,
    _dwSampleOleMisc,
    _tlid,
    _wVerMajor,
    _wVerMinor);

else
    return AfxOleUnregisterClass(m_clsid,
    m_lpszProgID);

}
```

如果由控件的视觉对象中的向导生成控件项目的C++4.1 或更高版本，此标志已将会出现在你的代码。 需要注册的线程模型不不进行任何更改。

如果由早期版本的 controlwizard 可生成你的项目，您的现有代码将作为第六个参数具有一个布尔值。 如果现有的参数为 TRUE，将其更改为*afxRegInsertable | afxregapartmentthreading 改*。 如果现有的参数为 FALSE，将其更改为*afxregapartmentthreading 改*。

如果您的控件不遵循对单元模型线程处理规则，您必须通过*afxregapartmentthreading 改*此参数中。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
