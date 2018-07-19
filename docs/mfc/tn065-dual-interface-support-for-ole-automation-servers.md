---
title: TN065： 针对 OLE 自动化服务器的双重接口支持 |Microsoft 文档
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.ole
dev_langs:
- C++
helpviewer_keywords:
- dual interfaces [MFC], OLE Automation
- TN065 [MFC]
- ACDUAL sample [MFC]
- Automation servers [MFC], dual-interface support
ms.assetid: b5c8ed09-2f7f-483c-80fc-2a47ad896063
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e30be46aeab92f63f1b4cba593cda52bf9aeef9a
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122178"
---
# <a name="tn065-dual-interface-support-for-ole-automation-servers"></a>TN065：针对 OLE 自动化服务器的双重接口支持

> [!NOTE]
> 以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

本说明介绍如何将双重接口支持添加到基于 MFC 的 OLE 自动化服务器应用程序。 [ACDUAL](../visual-cpp-samples.md)示例阐释了双重接口支持和本说明中的代码示例摘自 ACDUAL。 此说明，如 DECLARE_DUAL_ERRORINFO、 DUAL_ERRORINFO_PART 和 IMPLEMENT_DUAL_ERRORINFO 中, 所述的宏的 ACDUAL 示例的一部分以及可以在 MFCDUAL 中找到。H。

## <a name="dual-interfaces"></a>双重接口

尽管 OLE 自动化让你能够实现`IDispatch`接口、 VTBL 接口或双重接口 （其中包含同时），Microsoft 强烈建议你实现双重接口，对所有公开 OLE 自动化对象。 双重接口通过具有明显优势`IDispatch`-只有或仅 VTBL 接口：

- 在编译时通过 VTBL 接口，或通过运行时绑定可以发生`IDispatch`。

- 可以使用 VTBL 接口的 OLE 自动化控制器可能受益于提高性能。

- 使用的现有 OLE 自动化控制器`IDispatch`接口将继续工作。

- VTBL 接口是更轻松地从 c + + 调用。

- 双重接口所需的与 Visual Basic 对象支持功能的兼容性。

## <a name="adding-dual-interface-support-to-a-ccmdtarget-based-class"></a>将双重接口支持添加到基于 CCmdTarget 类

双重接口是一个自定义派生自接口实际上只是`IDispatch`。 若要实现中的双重接口支持的最直接方式`CCmdTarget`-基于的类是第一个实现正常调度使用 MFC 和 ClassWizard，类接口，然后在以后添加自定义的接口。 大多数情况下，你自定义接口的实现会将只需委托回 MFC`IDispatch`实现。

首先，修改你的服务器定义为您的对象的双重接口的 ODL 文件。 若要定义双重接口，必须使用接口语句，而不是`DISPINTERFACE`Visual c + + 向导生成的语句。 而不是删除现有`DISPINTERFACE`语句中，添加新的接口语句。 通过保留`DISPINTERFACE`窗体中，你可以继续使用 ClassWizard 将属性和方法添加到你的对象，但必须将等效的属性和方法添加到接口语句。

双重接口的接口语句必须具有*OLEAUTOMATION*和*双重*属性和接口必须派生自`IDispatch`。 你可以使用[GUIDGEN](../visual-cpp-samples.md)示例，用于创建**IID**双重接口：

```IDL
[ uuid(0BDD0E81-0DD7-11cf-BBA8-444553540000), // IID_IDualAClick
    oleautomation,
    dual
]
interface IDualAClick : IDispatch
    {
    };
```

一旦你准备好接口语句，启动添加的方法和属性的条目。 双重接口，对于，你需要重新排列参数列表，使你的方法和双重接口中的属性访问器函数将返回**HRESULT**并将其返回值作为参数具有属性传递`[retval,out]`. 请记住，对于属性，你将需要添加这两个读取 (`propget`) 和写入 (`propput`) 访问具有相同 id 的函数。例如：

```IDL
[propput, id(1)] HRESULT text([in] BSTR newText);
[propget, id(1)] HRESULT text([out, retval] BSTR* retval);
```

定义方法和属性后，你需要组件类语句中添加对接口语句的引用。 例如：

```IDL
[ uuid(4B115281-32F0-11cf-AC85-444553540000) ]
coclass Document
{
    dispinterface IAClick;
    [default] interface IDualAClick;
};
```

后已更新 ODL 文件，使用 MFC 的接口映射机制来在对象类中定义的双重接口的实现类和对应的条目中 MFC 的`QueryInterface`机制。 你需要中的一项`INTERFACE_PART`ODL，接口语句中的每个条目以及调度接口的条目的块。 与每个 ODL 条目*propput*属性需要一个名为函数`put_propertyname`。 与每个条目*propget*属性需要一个名为函数`get_propertyname`。

若要定义你的双重接口的实现类，添加`DUAL_INTERFACE_PART`到你的对象类定义的块。 例如：

```cpp
BEGIN_DUAL_INTERFACE_PART(DualAClick, IDualAClick)
    STDMETHOD(put_text)(THIS_ BSTR newText);
    STDMETHOD(get_text)(THIS_ BSTR FAR* retval);
    STDMETHOD(put_x)(THIS_ short newX);
    STDMETHOD(get_x)(THIS_ short FAR* retval);
    STDMETHOD(put_y)(THIS_ short newY);
    STDMETHOD(get_y)(THIS_ short FAR* retval);
    STDMETHOD(put_Position)(THIS_ IDualAutoClickPoint FAR* newPosition);
    STDMETHOD(get_Position)(THIS_ IDualAutoClickPoint FAR* FAR* retval);
    STDMETHOD(RefreshWindow)(THIS);
    STDMETHOD(SetAllProps)(THIS_ short x, short y, BSTR text);
    STDMETHOD(ShowWindow)(THIS);
END_DUAL_INTERFACE_PART(DualAClick)
```

若要连接到 MFC 的双重接口[QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms687230)机制，添加`INTERFACE_PART`到接口映射的条目：

```cpp
BEGIN_INTERFACE_MAP(CAutoClickDoc, CDocument)
    INTERFACE_PART(CAutoClickDoc, DIID_IAClick, Dispatch)
    INTERFACE_PART(CAutoClickDoc, IID_IDualAClick, DualAClick)
END_INTERFACE_MAP()
```

接下来，你需要填写接口的实现。 大多数情况下，你将能够将委托给现有 MFC`IDispatch`实现。 例如：

```cpp
STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::AddRef()
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    return pThis->ExternalAddRef();
}

STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::Release()
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    return pThis->ExternalRelease();
}

STDMETHODIMP CAutoClickDoc::XDualAClick::QueryInterface(
    REFIID iid,
    LPVOID* ppvObj)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    return pThis->ExternalQueryInterface(&iid, ppvObj);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfoCount(
    UINT FAR* pctinfo)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);
    return lpDispatch->GetTypeInfoCount(pctinfo);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfo(
    UINT itinfo,
    LCID lcid,
    ITypeInfo FAR* FAR* pptinfo)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetTypeInfo(itinfo, lcid, pptinfo);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::GetIDsOfNames(
    REFIID riid,
    OLECHAR FAR* FAR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID FAR* rgdispid)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetIDsOfNames(riid, rgszNames, cNames, lcid, rgdispid);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::Invoke(
    DISPID dispidMember,
    REFIID riid,
    LCID lcid,
    WORD wFlags,
    DISPPARAMS FAR* pdispparams,
    VARIANT FAR* pvarResult,
    EXCEPINFO FAR* pexcepinfo,
    UINT FAR* puArgErr)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);

    return lpDispatch->Invoke(dispidMember, riid, lcid,
        wFlags, pdispparams, pvarResult, pexcepinfo, puArgErr);
}
```

对于对象的方法和属性访问器函数，你需要填写实现。 通常，您方法和属性的函数可以委派回使用类向导生成的方法。 但是，如果将属性设置为直接访问的变量，你需要编写代码以 get/put 值到变量。 例如：

```cpp
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    // MFC automatically converts from Unicode BSTR to
    // Ansi CString, if necessary...
    pThis->m_str = newText;
    return NOERROR;
}

STDMETHODIMP CAutoClickDoc::XDualAClick::get_text(BSTR* retval)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    // MFC automatically converts from Ansi CString to
    // Unicode BSTR, if necessary...
    pThis->m_str.SetSysString(retval);
    return NOERROR;
}
```

## <a name="passing-dual-interface-pointers"></a>传递双重接口指针

传递双重接口指针不简单，特别是如果你需要调用`CCmdTarget::FromIDispatch`。 `FromIDispatch` 仅适用于 MFC 的`IDispatch`指针。 要解决此问题的一种方法是适用于原始查询`IDispatch`指针集由 MFC 并将该指针传递给需要它的函数。 例如：

```
STDMETHODIMP CAutoClickDoc::XDualAClick::put_Position(
    IDualAutoClickPoint FAR* newPosition)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDisp = NULL;
    newPosition->QueryInterface(IID_IDispatch, (LPVOID*)&lpDisp);
    pThis->SetPosition(lpDisp);
    lpDisp->Release();
    return NOERROR;
}
```

之前通过双重接口方法向回传递一个指针，你可能需要将其从 MFC 转换`IDispatch`指向双重接口指针。 例如：

```
STDMETHODIMP CAutoClickDoc::XDualAClick::get_Position(
    IDualAutoClickPoint FAR* FAR* retval)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDisp;
    lpDisp = pThis->GetPosition();
    lpDisp->QueryInterface(IID_IDualAutoClickPoint, (LPVOID*)retval);
    return NOERROR;
}
```

## <a name="registering-the-applications-type-library"></a>注册应用程序的类型库

应用程序向导不会生成代码以向系统注册 OLE 自动化服务器应用程序的类型库。 虽然有其他方法可注册类型库，很方便地将注册的类型库，当独立运行应用程序时，它正在，即更新其 OLE 类型信息，该应用程序。

注册应用程序的类型库只要运行应用程序单独存在：

- 包括 AFXCTL。在你标准 H 包括标头文件，STDAFX。H，若要访问的定义`AfxOleRegisterTypeLib`函数。

- 应用程序中`InitInstance`函数中，找到调用`COleObjectFactory::UpdateRegistryAll`。 此调用后添加对的调用`AfxOleRegisterTypeLib`，并指定**LIBID**对应于你的类型库，以及你的类型库的名称：

    ```cpp
    // When a server application is launched stand-alone, it is a good idea
    // to update the system registry in case it has been damaged.
    m_server.UpdateRegistry(OAT_DISPATCH_OBJECT);

    COleObjectFactory::UpdateRegistryAll();

    // DUAL_SUPPORT_START
        // Make sure the type library is registered or dual interface won't work.
        AfxOleRegisterTypeLib(AfxGetInstanceHandle(),
            LIBID_ACDual,
            _T("AutoClik.TLB"));
    // DUAL_SUPPORT_END
    ```

## <a name="modifying-project-build-settings-to-accommodate-type-library-changes"></a>修改项目生成设置，以容纳类型库的更改

若要修改的项目的生成设置，以便标头文件包含**UUID**由 MkTypLib 生成定义，每当重新生成类型库：

1. 上**生成**菜单上，单击**设置**，然后从每个配置文件列表中选择 ODL 文件。

2. 单击**OLE 类型**选项卡上，并指定是中的文件名**输出标头**filename 字段。 因为 MkTypLib 将覆盖任何现有文件，请使用未由你项目中，已使用的文件名。 单击**确定**关闭**生成设置**对话框。

若要添加**UUID**从 MkTypLib 生成标头文件到你的项目的定义：

1. 包括 MkTypLib 生成你的标准中的标头文件包含头文件，STDAFX。H。

2. 创建一个新文件，INITIIDS。CPP，并将其添加到你的项目。 在此文件中，包括 OLE2 之后包括 MkTypLib 生成标头文件。H 和 INITGUID。H:

    ```cpp
    // initIIDs.c: defines IIDs for dual interfaces
    // This must not be built with precompiled header.
    #include <ole2.h>
    #include <initguid.h>
    #include "acdual.h"
    ```

3. 上**生成**菜单上，单击**设置**，然后选择 INITIIDS。从文件列表中为每个配置的 CPP。

4. 单击**c + +** 选项卡上，单击类别**预编译标头**，然后选择**不使用预编译标头**单选按钮。 单击确定以关闭**生成设置**对话框。

## <a name="specifying-the-correct-object-class-name-in-the-type-library"></a>在类型库中指定正确的对象类名称

不正确地随 Visual c + + 向导使用的实现类名称组件类文件中指定服务器的 ODL 作为 OLE 可创建类。 尽管这也可以生效，实现类名称可能不是对象的你希望你的用户使用的类名称。 若要指定正确的名称，打开 ODL 文件，找到每个组件类语句，并将实现类名称替换为相应的外部名称。

请注意，当更改组件类语句时，变量名称的**CLSID**MkTypLib 生成标头文件中的 s 将相应地更改。 你将需要更新你的代码以使用新的变量名称。

## <a name="handling-exceptions-and-the-automation-error-interfaces"></a>处理的异常和自动化错误接口

您的自动化对象的方法和属性访问器函数可能会引发异常。 如果这样，你应在你的双重接口实现中处理这些，并将有关异常的信息传递回通过 OLE 自动化错误处理接口，控制器`IErrorInfo`。 此接口提供的详细、 上下文错误信息通过`IDispatch`和 VTBL 接口。 若要指示错误处理程序将提供，则应实现`ISupportErrorInfo`接口。

为了说明的错误处理机制，假定用来实现的标准调度支持 ClassWizard 生成函数引发异常。 MFC 的实现`IDispatch::Invoke`通常捕获这些异常并将它们转换为返回通过 EXCEPTINFO 结构`Invoke`调用。 但是，当使用 VTBL 接口时，则要负责自行捕获异常。 作为保护你的双重接口方法的示例：

```cpp
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    TRY_DUAL(IID_IDualAClick)
    {
        // MFC automatically converts from Unicode BSTR to
        // Ansi CString, if necessary...
        pThis->m_str = newText;
        return NOERROR;
    }
    CATCH_ALL_DUAL
}
```

`CATCH_ALL_DUAL` 负责返回正确的错误代码发生异常时。 `CATCH_ALL_DUAL` 将 MFC 异常转换为 OLE 自动化错误处理信息使用`ICreateErrorInfo`接口。 (示例`CATCH_ALL_DUAL`宏位于文件 MFCDUAL。中的 H [ACDUAL](../visual-cpp-samples.md)示例。 它调用来处理异常，该函数`DualHandleException`，MFCDUAL 的文件中。CPP。)`CATCH_ALL_DUAL`确定要返回基于发生的异常的类型的错误代码：

- [COleDispatchException](../mfc/reference/coledispatchexception-class.md) -在这种情况下，`HRESULT`使用下面的代码构造：

    ```cpp
    hr = MAKE_HRESULT(SEVERITY_ERROR, FACILITY_ITF, (e->m_wCode + 0x200));
    ```

     这将创建`HRESULT`特定于导致异常的接口。 错误代码减去 0x200 以避免与系统定义的任何冲突`HRESULT`标准 OLE 接口的 s。

- [CMemoryException](../mfc/reference/cmemoryexception-class.md) -在这种情况下，`E_OUTOFMEMORY`返回。

- 任何其他异常 – 在此情况下，`E_UNEXPECTED`返回。

若要指示使用 OLE 自动化错误处理程序，还应实现`ISupportErrorInfo`接口。

首先，将代码添加到你的自动化类定义，以表明它支持`ISupportErrorInfo`。

其次，将代码添加到您的自动化类的接口映射关联`ISupportErrorInfo`与 MFC 的实现类`QueryInterface`机制。 `INTERFACE_PART`语句为定义的类匹配`ISupportErrorInfo`。

最后，实现定义的用于支持类`ISupportErrorInfo`。

( [ACDUAL](../visual-cpp-samples.md)示例包含三个宏，以帮助执行这三个步骤， `DECLARE_DUAL_ERRORINFO`， `DUAL_ERRORINFO_PART`，和`IMPLEMENT_DUAL_ERRORINFO`，所有包含在 MFCDUAL。H。)

下面的示例实现类定义以支持`ISupportErrorInfo`。 `CAutoClickDoc` 是你的自动化类的名称和`IID_IDualAClick`是**IID**的接口，是通过 OLE 自动化错误对象报告的错误源：

```cpp
STDMETHODIMP_(ULONG) CAutoClickDoc::XSupportErrorInfo::AddRef()
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return pThis->ExternalAddRef();
}

STDMETHODIMP_(ULONG) CAutoClickDoc::XSupportErrorInfo::Release()
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return pThis->ExternalRelease();
}

STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::QueryInterface(
    REFIID iid,
    LPVOID* ppvObj)
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return pThis->ExternalQueryInterface(&iid, ppvObj);
}

STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::InterfaceSupportsErrorInfo(
    REFIID iid)
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return (iid == IID_IDualAClick) S_OK : S_FALSE;
}
```

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)  
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)  
