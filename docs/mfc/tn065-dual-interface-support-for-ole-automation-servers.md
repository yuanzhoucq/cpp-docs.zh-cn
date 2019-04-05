---
title: TN065:针对 OLE 自动化服务器的双重接口支持
ms.date: 06/28/2018
f1_keywords:
- vc.ole
helpviewer_keywords:
- dual interfaces [MFC], OLE Automation
- TN065 [MFC]
- ACDUAL sample [MFC]
- Automation servers [MFC], dual-interface support
ms.assetid: b5c8ed09-2f7f-483c-80fc-2a47ad896063
ms.openlocfilehash: 33828f3979fb938ae6e88fa3cb0d6ee24daa958c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "58776669"
---
# <a name="tn065-dual-interface-support-for-ole-automation-servers"></a>TN065:针对 OLE 自动化服务器的双重接口支持

> [!NOTE]
> 以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

本说明讨论如何向基于 MFC 的 OLE 自动化服务器应用程序添加双重接口支持。 [ACDUAL](../overview/visual-cpp-samples.md)示例说明了双重接口支持和本说明中的代码示例摘自 ACDUAL。 此说明，例如 DECLARE_DUAL_ERRORINFO、 DUAL_ERRORINFO_PART 和 IMPLEMENT_DUAL_ERRORINFO 中, 所述的宏的 ACDUAL 示例以及可在 MFCDUAL 中找到。H.

## <a name="dual-interfaces"></a>双重接口

尽管 OLE 自动化，可实现`IDispatch`接口、 VTBL 接口或双重接口 （其中包含同时），Microsoft 强烈建议为所有公开 OLE 自动化对象实现双重接口。 双重接口通过具有明显的优点`IDispatch`-唯一或仅限 VTBL 的接口：

- 在编译时通过 VTBL 接口，或通过运行时绑定可以发生`IDispatch`。

- 可以使用 VTBL 接口的 OLE 自动化控制器可能受益于改进的性能。

- 使用的现有 OLE 自动化控制器`IDispatch`接口将继续工作。

- VTBL 接口是更轻松地从 c + + 调用。

- 双重接口所需的与 Visual Basic 对象支持功能的兼容性。

## <a name="adding-dual-interface-support-to-a-ccmdtarget-based-class"></a>将双重接口支持添加到基于 CCmdTarget 类

双重接口是一个自定义派生自接口实际上只是`IDispatch`。 最简单的方法实现中的双重接口支持`CCmdTarget`-基于的类是为第一个实现正常调度接口上使用 MFC 和类向导，您的类，然后添加自定义接口更高版本。 大多数情况下，您的自定义接口的实现只需委托到 MFC`IDispatch`实现。

首先，修改你的服务器定义为对象的双重接口 ODL 文件。 若要定义双重接口，必须使用接口语句，而不是`DISPINTERFACE`Visual c + + 向导生成的语句。 而不是删除现有`DISPINTERFACE`语句中，添加新的接口语句。 通过保留`DISPINTERFACE`窗体中，您可以继续使用类向导将属性和方法添加到您的对象，但必须将等效属性和方法添加到接口语句。

双重接口的接口语句必须具有*OLEAUTOMATION*并*双*属性，该接口必须派生自`IDispatch`。 可以使用[GUIDGEN](../overview/visual-cpp-samples.md)示例来创建**IID**为双重接口：

```IDL
[ uuid(0BDD0E81-0DD7-11cf-BBA8-444553540000), // IID_IDualAClick
    oleautomation,
    dual
]
interface IDualAClick : IDispatch
    {
    };
```

一旦了接口语句，开始添加的方法和属性的条目。 需要重新排列参数列表，以便你的方法和属性访问器函数中的双重接口返回的双重接口**HRESULT**并将其返回值作为参数的特性传递`[retval,out]`. 请记住，对于属性，您将需要添加这两个读取 (`propget`) 和写入 (`propput`) 访问具有相同 id 的函数。例如：

```IDL
[propput, id(1)] HRESULT text([in] BSTR newText);
[propget, id(1)] HRESULT text([out, retval] BSTR* retval);
```

定义方法和属性后，需要在 coclass 语句中添加对接口语句的引用。 例如：

```IDL
[ uuid(4B115281-32F0-11cf-AC85-444553540000) ]
coclass Document
{
    dispinterface IAClick;
    [default] interface IDualAClick;
};
```

一旦更新 ODL 文件，使用 MFC 的接口映射机制来定义对象类中的双重接口的实现类和在 MFC 中生成相应的条目`QueryInterface`机制。 所需的某一项`INTERFACE_PART`ODL，该接口语句中的每项加上调度接口的条目的块。 与每个 ODL 条目*propput*属性需要一个名为函数`put_propertyname`。 与每个条目*propget*属性需要一个名为函数`get_propertyname`。

若要定义你的双重接口的实现类，添加`DUAL_INTERFACE_PART`对象类定义的块。 例如：

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

若要连接到 MFC 的双重接口[QueryInterface](/windows/desktop/com/queryinterface--navigating-in-an-object)机制，添加`INTERFACE_PART`到接口映射的条目：

```cpp
BEGIN_INTERFACE_MAP(CAutoClickDoc, CDocument)
    INTERFACE_PART(CAutoClickDoc, DIID_IAClick, Dispatch)
    INTERFACE_PART(CAutoClickDoc, IID_IDualAClick, DualAClick)
END_INTERFACE_MAP()
```

接下来，您需要填写接口的实现。 大多数情况下，你将能够将委托给现有 MFC`IDispatch`实现。 例如：

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

对于对象的方法和属性访问器函数，您需要填充实现代码。 通常，您方法和属性的函数可以委派回使用类向导所生成的方法。 但是，如果将属性设置直接访问的变量，则需要编写代码以 get/put 值到变量。 例如：

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

## <a name="passing-dual-interface-pointers"></a>将双重接口指针传递

双重接口指针传递并不那么容易，尤其是当您需要调用`CCmdTarget::FromIDispatch`。 `FromIDispatch` 仅适用于 MFC 的`IDispatch`指针。 解决此问题的一种方法是查询的原始`IDispatch`指针集由 MFC 并将该指针传递给需要它的函数。 例如：

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

然后再将指针传递回通过双重接口方法，您可能需要将其转换从 MFC`IDispatch`为双重接口指针的指针。 例如：

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

应用程序向导不会生成代码以向系统注册 OLE 自动化服务器应用程序的类型库。 虽然有注册类型库的其他方法，可以很方便让应用程序在更新其 OLE 的类型信息，也就是说，每当独立运行应用程序时注册类型库。

若要注册应用程序的类型库时运行该应用程序单独存在：

- 包括 AFXCTL。在您的标准 H 包括 STDAFX 的头文件。H，若要访问的定义`AfxOleRegisterTypeLib`函数。

- 在应用程序的`InitInstance`函数中，找到调用`COleObjectFactory::UpdateRegistryAll`。 此调用后添加对的调用`AfxOleRegisterTypeLib`，并指定**LIBID**对应于你的类型库，以及类型库的名称：

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

## <a name="modifying-project-build-settings-to-accommodate-type-library-changes"></a>修改项目生成设置，以适应类型库的更改

若要修改项目的生成设置，以便一个标头文件，其中包含**UUID** MkTypLib 由生成定义，只要重新生成类型库：

1. 上**构建**菜单上，单击**设置**，然后选择从文件列表中为每个配置的 ODL 文件。

2. 单击**OLE 类型**选项卡上，并指定是中的文件名**输出标头**文件名字段。 使用你的项目，已不使用的文件名，因为 MkTypLib 将覆盖任何现有文件。 单击**确定**以关闭**生成设置**对话框。

若要添加**UUID** MkTypLib 生成标头文件中定义到你的项目：

1. 包括由 MkTypLib 生成您的标准中的标头文件包括标头文件，STDAFX。H.

2. 创建新文件，INITIIDS。CPP，并将其添加到你的项目。 在此文件中，包含 OLE2 后包括 MkTypLib 生成标头文件。H 和 INITGUID。H:

    ```cpp
    // initIIDs.c: defines IIDs for dual interfaces
    // This must not be built with precompiled header.
    #include <ole2.h>
    #include <initguid.h>
    #include "acdual.h"
    ```

3. 上**构建**菜单上，单击**设置**，然后选择 INITIIDS。CPP 文件列表中的每个配置。

4. 单击**c + +** 选项卡上，单击类别**预编译标头**，然后选择**不使用预编译标头**单选按钮。 单击确定以关闭**生成设置**对话框。

## <a name="specifying-the-correct-object-class-name-in-the-type-library"></a>类型库中指定正确的对象类名称

错误地随 Visual c + + 向导使用实现类名称服务器的 OLE 可创建类 ODL 文件中指定组件类。 尽管这也可以生效，实现类名可能不是所需对象的用户使用的类名称。 若要指定正确的名称，打开 ODL 文件，找到每个 coclass 语句，并实现类名称替换为正确的外部名称。

请注意，当更改 coclass 语句时，变量的名称**CLSID**MkTypLib 生成标头文件中将相应地更改。 你将需要更新代码以使用新的变量名称。

## <a name="handling-exceptions-and-the-automation-error-interfaces"></a>处理异常和自动化错误接口

自动化对象的方法和属性访问器函数可能会引发异常。 如果因此，应在双重接口实现中处理它们，并将有关异常的信息传递回通过 OLE 自动化错误处理接口，控制器`IErrorInfo`。 此接口提供的详细、 上下文错误信息通过`IDispatch`和 VTBL 接口。 若要指示错误处理程序可用，则应实现`ISupportErrorInfo`接口。

为了说明的错误处理机制，假定类向导生成的函数，用于实现的标准调度支持，引发异常。 MFC 的实现`IDispatch::Invoke`通常捕获这些异常并将它们通过返回 EXCEPTINFO 结构转换为`Invoke`调用。 但是，当使用 VTBL 接口时，则要负责自行捕获异常。 作为保护您的双接口方法的示例：

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

`CATCH_ALL_DUAL` 负责发生异常时返回正确的错误代码。 `CATCH_ALL_DUAL` 将 MFC 异常转换为 OLE 自动化错误处理的信息，并使用`ICreateErrorInfo`接口。 (示例`CATCH_ALL_DUAL`宏是 MFCDUAL 在文件中。中的 H [ACDUAL](../overview/visual-cpp-samples.md)示例。 它调用来处理异常，该函数`DualHandleException`，MFCDUAL 文件中。CPP。)`CATCH_ALL_DUAL`确定要返回基于所发生的异常类型的错误代码：

- [COleDispatchException](../mfc/reference/coledispatchexception-class.md) -在这种情况下，`HRESULT`使用以下代码构造：

    ```cpp
    hr = MAKE_HRESULT(SEVERITY_ERROR, FACILITY_ITF, (e->m_wCode + 0x200));
    ```

   这将创建`HRESULT`特定于导致异常的接口。 错误代码偏移 0x200 以避免与系统定义的任何冲突的`HRESULT`标准 OLE 接口的 s。

- [CMemoryException](../mfc/reference/cmemoryexception-class.md) -在这种情况下，`E_OUTOFMEMORY`返回。

- 任何其他异常-在本例中为`E_UNEXPECTED`返回。

若要指示使用 OLE 自动化错误处理程序，还应实现`ISupportErrorInfo`接口。

首先，将代码添加到你的自动化类定义以表明它支持`ISupportErrorInfo`。

其次，将代码添加到您的自动化类的接口映射来将相关联`ISupportErrorInfo`与 MFC 的实现类`QueryInterface`机制。 `INTERFACE_PART`语句与为定义的类匹配`ISupportErrorInfo`。

最后，实现类定义以支持`ISupportErrorInfo`。

( [ACDUAL](../overview/visual-cpp-samples.md)示例包含三个宏，以帮助执行这三个步骤`DECLARE_DUAL_ERRORINFO`， `DUAL_ERRORINFO_PART`，和`IMPLEMENT_DUAL_ERRORINFO`、 MFCDUAL 中包含的所有。H.)

下面的示例实现一个类定义以支持`ISupportErrorInfo`。 `CAutoClickDoc` 是自动化类的名称和`IID_IDualAClick`是**IID**是通过 OLE 自动化错误对象报告的错误源的接口：

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

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
