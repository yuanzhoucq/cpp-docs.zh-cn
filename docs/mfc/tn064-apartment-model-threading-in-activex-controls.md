---
title: TN064：ActiveX 控件中的单元模型线程处理
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
ms.openlocfilehash: 2c6b9dd3ed244f7169e5055eebe7a34e3345e841
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513322"
---
# <a name="tn064-apartment-model-threading-in-activex-controls"></a>TN064：ActiveX 控件中的单元模型线程处理

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

本技术说明介绍了如何在 ActiveX 控件中启用单元模型线程处理。 请注意, 仅在 Visual C++版本4.2 或更高版本中支持单元模型线程处理。

## <a name="what-is-apartment-model-threading"></a>什么是单元模型线程

单元模型是一种在多线程容器应用程序中支持嵌入对象 (如 ActiveX 控件) 的方法。 尽管应用程序可能有多个线程, 但嵌入对象的每个实例都将分配给一个 "单元", 后者将只在一个线程上执行。 换句话说, 对控件实例的所有调用都将在同一线程上发生。

但是, 可以将相同类型的控件的不同实例分配给不同的单元。 因此, 如果控件的多个实例共享公共数据 (例如静态数据或全局数据), 则对此共享数据的访问需要由同步对象 (如临界区) 来保护。

有关单元线程模型的完整详细信息, 请参阅*OLE 程序员参考*中的[进程和线程](/windows/win32/ProcThread/processes-and-threads)。

## <a name="why-support-apartment-model-threading"></a>为什么支持单元模型线程

支持单元模型线程的控件可用于也支持单元模型的多线程容器应用程序。 如果未启用单元模型线程处理, 则将限制可在其中使用控件的可能的容器集。

为大多数控件启用单元模型线程处理非常简单, 特别是在这些控件有少量或没有共享数据的情况下。

## <a name="protecting-shared-data"></a>保护共享数据

如果控件使用共享数据 (如静态成员变量), 则应使用临界区保护对该数据的访问, 以防止多个线程同时修改数据。 若要为此目的设置关键部分, 请在控件的类中声明类`CCriticalSection`的静态成员变量。 如果代码访问`Unlock`共享数据,请使用此临界区对象的和成员函数。`Lock`

例如, 请考虑需要维护所有实例共享的字符串的控件类。 此字符串可在静态成员变量中进行维护并受临界区的保护。 控件的类声明将包含以下内容:

```
class CSampleCtrl : public COleControl
{
...
    static CString _strShared;
    static CCriticalSection _critSect;
};
```

类的实现将包括这些变量的定义:

```
int CString CSampleCtrl::_strShared;
CCriticalSection CSampleCtrl::_critSect;
```

然后, 可以`_strShared`通过临界区保护对静态成员的访问:

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

## <a name="registering-an-apartment-model-aware-control"></a>注册单元模型感知控件

支持单元模型线程的控件应通过在*类 id* \\ **下的类 id 注册表项中添加值为 "单元" 的命名值 "ThreadingModel" 来指示此功能。InprocServer32**键。 若要使此密钥自动注册到你的控件, 请将第六个参数中的 afxregapartmentthreading 改`AfxOleRegisterControlClass`标志传递给:

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

如果你的控件项目是在 Visual C++版本4.1 或更高版本中由 ControlWizard 生成的, 则你的代码中已存在此标志。 无需进行任何更改即可注册线程模型。

如果你的项目是由早期版本的 ControlWizard 生成的, 则你的现有代码将包含一个布尔值作为第六个参数。 如果现有参数为 TRUE, 则将其更改为*afxRegInsertable | afxregapartmentthreading 改*。 如果现有参数为 FALSE, 请将其更改为*afxregapartmentthreading 改*。

如果控件未遵循单元模型线程处理规则, 则不能在此参数中传递*afxregapartmentthreading 改*。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
