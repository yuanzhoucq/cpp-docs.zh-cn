---
title: TN064：ActiveX 控件中的单元模型线程
ms.date: 11/04/2016
helpviewer_keywords:
- OLE controls [MFC], container support
- containers [MFC], multithreaded
- TN064 [MFC]
- multithread container [MFC]
- apartment model threading [MFC]
ms.assetid: b2ab4c88-6954-48e2-9a74-01d4a60df073
ms.openlocfilehash: 0c6a42124b4b2b03ae7cd9277fa14d43eac7a2bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366060"
---
# <a name="tn064-apartment-model-threading-in-activex-controls"></a>TN064：ActiveX 控件中的单元模型线程

> [!NOTE]
> 以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

本技术说明说明如何在 ActiveX 控件中启用公寓模型线程。 请注意，公寓模型线程仅在视觉C++版本 4.2 或更高版本中支持。

## <a name="what-is-apartment-model-threading"></a>什么是公寓-模型线程

单元模型是支持多线程容器应用程序中的嵌入式对象（如 ActiveX 控件）的方法。 尽管应用程序可能有多个线程，但嵌入对象的每个实例都将分配给一个"单元"，该"单元"将仅在一个线程上执行。 换句话说，对控件实例的所有调用都将在同一线程上发生。

但是，同一类型的控制的不同实例可能分配给不同的公寓。 因此，如果控件的多个实例共享任何通用数据（例如静态或全局数据），则需要通过同步对象（如关键部分）保护对此共享数据的访问。

有关公寓线程模型的完整详细信息，请参阅*OLE 程序员参考*中的["进程和线程](/windows/win32/ProcThread/processes-and-threads)"。

## <a name="why-support-apartment-model-threading"></a>为什么支持公寓-模型线程

支持单元模型线程的控件可用于支持单元模型的多线程容器应用程序。 如果不启用公寓模型线程，将限制可以使用控件的潜在容器集。

对于大多数控件来说，启用公寓模型线程很容易，尤其是当它们几乎没有共享数据时。

## <a name="protecting-shared-data"></a>保护共享数据

如果控件使用共享数据（如静态成员变量），则应使用关键部分保护对该数据的访问，以防止多个线程同时修改数据。 为此设置关键部分，请声明控件类中的类`CCriticalSection`的静态成员变量。 无论代码`Lock`访问`Unlock`共享数据的位置，都使用此关键部分对象的 和 成员函数。

例如，考虑需要维护由所有实例共享的字符串的控件类。 此字符串可以保存在静态成员变量中，并由关键部分保护。 控件的类声明将包含以下内容：

```cpp
class CSampleCtrl : public COleControl
{
...
    static CString _strShared;
    static CCriticalSection _critSect;
};
```

类的实现将包括这些变量的定义：

```cpp
int CString CSampleCtrl::_strShared;
CCriticalSection CSampleCtrl::_critSect;
```

然后，可以通过`_strShared`关键部分保护对静态成员的访问：

```cpp
void CSampleCtrl::SomeMethod()
{
    _critSect.Lock();
if (_strShared.Empty())
    _strShared = "<text>";
    _critSect.Unlock();

...
}
```

## <a name="registering-an-apartment-model-aware-control"></a>注册公寓模型感知控制

支持公寓模型线程的控件应在注册表中指示此功能，在*类 ID*\\**InprocServer32**键下的类 ID 注册表条目中添加具有"公寓"值的命名值"线程模型"。 要使此密钥自动注册以进行控制，请将第六个参数中的*afxReg公寓线程*标志传递给`AfxOleRegisterControlClass`：

```cpp
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

如果控件项目由 VisualC++ 版 4.1 或更高版本的 ControlWizard 生成，则此标志将已经在代码中存在。 注册线程模型不需要任何更改。

如果项目由早期版本的 ControlWizard 生成，则现有代码将具有布尔值作为第六个参数。 如果现有参数为 TRUE，请将其更改为*afxReg 可插入 = afxReg公寓线程*。 如果现有参数为 FALSE，则将其更改为*afxReg公寓线程*。

如果您的控件未遵循公寓模型线程的规则，则不得在此参数中传递*afxReg公寓线程*。

## <a name="see-also"></a>另请参阅

[技术说明（按编号）](../mfc/technical-notes-by-number.md)<br/>
[按类别分类的技术说明](../mfc/technical-notes-by-category.md)
