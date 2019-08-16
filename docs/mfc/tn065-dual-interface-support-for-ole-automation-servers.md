---
title: TN065：对 OLE 自动化服务器的双重接口支持
ms.date: 06/28/2018
f1_keywords:
- vc.ole
helpviewer_keywords:
- dual interfaces [MFC], OLE Automation
- TN065 [MFC]
- ACDUAL sample [MFC]
- Automation servers [MFC], dual-interface support
ms.assetid: b5c8ed09-2f7f-483c-80fc-2a47ad896063
ms.openlocfilehash: afcbfd643d8b931e61b0f011b66482be5b2bcc82
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510995"
---
# <a name="tn065-dual-interface-support-for-ole-automation-servers"></a>TN065：对 OLE 自动化服务器的双重接口支持

> [!NOTE]
> 以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

此说明讨论了如何向基于 MFC 的 OLE 自动化服务器应用程序添加双重接口支持。 [ACDUAL](../overview/visual-cpp-samples.md)示例演示了双重接口支持, 并从 ACDUAL 中获取了此注释中的示例代码。 本说明中描述的宏 (如 DECLARE_DUAL_ERRORINFO、DUAL_ERRORINFO_PART 和 IMPLEMENT_DUAL_ERRORINFO) 是 ACDUAL 示例的一部分, 可在 MFCDUAL.H 中找到。高.

## <a name="dual-interfaces"></a>双重接口

虽然 OLE 自动化允许实现`IDispatch`接口、VTBL 接口或双重接口 (包含两者), 但 Microsoft 强烈建议为所有公开的 OLE 自动化对象实现双重接口。 双重接口的优点优于`IDispatch`或仅限 VTBL 接口:

- 绑定可在编译时通过 VTBL 接口进行, 或在运行时通过`IDispatch`。

- 可使用 VTBL 接口的 OLE 自动化控制器可能会受益于改进的性能。

- 使用`IDispatch`接口的现有 OLE 自动化控制器将继续工作。

- 可以更轻松地从C++VTBL 接口调用。

- 与 Visual Basic 对象支持功能兼容需要双重接口。

## <a name="adding-dual-interface-support-to-a-ccmdtarget-based-class"></a>向基于 CCmdTarget 的类添加双重接口支持

双重接口实际上只是派生`IDispatch`自的自定义接口。 若要在基于的`CCmdTarget`类中实现双重接口支持, 最直接的方法是先使用 MFC 和 ClassWizard 实现类的正常调度接口, 然后再添加自定义接口。 大多数情况下, 自定义接口实现仅委托回 MFC `IDispatch`实现。

首先, 修改服务器的 ODL 文件, 为对象定义双重接口。 若要定义双重接口, 必须使用 interface 语句, 而不是`DISPINTERFACE`可视化C++向导生成的语句。 添加新的 interface 语句`DISPINTERFACE` , 而不是删除现有语句。 通过保留`DISPINTERFACE`窗体, 可以继续使用 ClassWizard 向对象添加属性和方法, 但必须将等效的属性和方法添加到 interface 语句中。

双重接口的接口语句必须具有*OLEAUTOMATION*和*双重*特性, 并且接口必须派生自`IDispatch`。 可以使用[guidgen.exe](../overview/visual-cpp-samples.md)示例为双重接口创建**IID** :

```IDL
[ uuid(0BDD0E81-0DD7-11cf-BBA8-444553540000), // IID_IDualAClick
    oleautomation,
    dual
]
interface IDualAClick : IDispatch
    {
    };
```

接口语句准备就绪后, 开始添加方法和属性的项。 对于双重接口, 需要重新排列参数列表, 以便双重接口中的方法和属性访问器函数返回**HRESULT**并将它们的返回值作为参数传递给特性`[retval,out]`。 请记住, 对于属性, 将需要添加具有相同 id 的 read`propget`() 和 write`propput`() 访问函数。例如:

```IDL
[propput, id(1)] HRESULT text([in] BSTR newText);
[propget, id(1)] HRESULT text([out, retval] BSTR* retval);
```

定义方法和属性后, 需要在 coclass 语句中添加对 interface 语句的引用。 例如:

```IDL
[ uuid(4B115281-32F0-11cf-AC85-444553540000) ]
coclass Document
{
    dispinterface IAClick;
    [default] interface IDualAClick;
};
```

更新 ODL 文件后, 使用 mfc 的接口映射机制在对象类中为双重接口定义实现类, 并在 MFC `QueryInterface`机制中设置相应的条目。 对于 ODL 的 interface 语句中`INTERFACE_PART`的每个条目, 都需要在块中输入一个条目, 再加上调度接口的条目。 具有*propput*属性的每个 ODL 条目都需要一个`put_propertyname`名为的函数。 具有*propget*属性的每个条目都需要一个`get_propertyname`名为的函数。

若要为双重接口定义实现类, 请向对象`DUAL_INTERFACE_PART`类定义添加块。 例如:

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

若要将双重接口连接到 MFC 的[QueryInterface](/windows/win32/com/queryinterface--navigating-in-an-object)机制, 请`INTERFACE_PART`将条目添加到接口映射:

```cpp
BEGIN_INTERFACE_MAP(CAutoClickDoc, CDocument)
    INTERFACE_PART(CAutoClickDoc, DIID_IAClick, Dispatch)
    INTERFACE_PART(CAutoClickDoc, IID_IDualAClick, DualAClick)
END_INTERFACE_MAP()
```

接下来, 需要填写接口的实现。 在大多数情况下, 你将能够委托到现有的 MFC `IDispatch`实现。 例如:

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

对于对象的方法和属性访问器函数, 需要填写实现。 方法和属性函数通常可以委托回使用 ClassWizard 生成的方法。 但是, 如果将属性设置为直接访问变量, 则需要编写代码以获取/将值放入该变量中。 例如:

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

传递双重接口指针并不简单, 特别是在需要调用`CCmdTarget::FromIDispatch`时。 `FromIDispatch`仅适用于 MFC 的`IDispatch`指针。 解决这种情况的一种方法是查询由 MFC `IDispatch`设置的原始指针, 并将该指针传递给需要它的函数。 例如:

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

在通过双重接口方法向后传递指针之前, 您可能需要将其从 MFC `IDispatch`指针转换为双重接口指针。 例如：

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

应用程序向导不会生成用于向系统注册 OLE 自动化服务器应用程序的类型库的代码。 尽管还有其他方法来注册类型库, 但使应用程序在更新其 OLE 类型信息时注册类型库是非常方便的, 也就是说, 每当应用程序独立运行时。

若要在应用程序独立运行时注册应用程序的类型库:

- 包括 AFXCTL.H。标准中的 H 包含头文件 STDAFX.H。H, 用于访问`AfxOleRegisterTypeLib`函数的定义。

- 在应用程序的`InitInstance`函数中, 找到对`COleObjectFactory::UpdateRegistryAll`的调用。 在此调用之后, 添加对`AfxOleRegisterTypeLib`的调用, 同时指定与类型库对应的**LIBID**以及类型库的名称:

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

## <a name="modifying-project-build-settings-to-accommodate-type-library-changes"></a>修改项目生成设置以容纳类型库更改

若要修改项目的生成设置, 以使包含**UUID**定义的标头文件在重新生成类型库时由 mktyplib.exe 生成:

1. 在 "**生成**" 菜单上, 单击 "**设置**", 然后从每个配置的文件列表中选择 ODL 文件。

2. 单击 " **OLE 类型**" 选项卡, 并在 "**输出头**文件名" 字段中指定一个文件名。 使用项目尚未使用的文件名, 因为 Mktyplib.exe 将覆盖任何现有文件。 单击 **"确定"** 关闭 "**生成设置**" 对话框。

若要将 Mktyplib.exe 生成的标头文件中的**UUID**定义添加到项目中, 请执行以下操作:

1. 在标准中包括 Mktyplib.exe 生成的标头文件包括头文件 STDAFX.H。高.

2. 创建新文件 INITIIDS。CPP, 并将其添加到你的项目中。 在此文件中, 包含 OLE2 后, 包括 Mktyplib.exe 生成的标头文件。H 和 INITGUID.H。高

    ```cpp
    // initIIDs.c: defines IIDs for dual interfaces
    // This must not be built with precompiled header.
    #include <ole2.h>
    #include <initguid.h>
    #include "acdual.h"
    ```

3. 在 "**生成**" 菜单上, 单击 "**设置**", 然后选择 "INITIIDS"。每个配置的文件列表中的 CPP。

4. 单击 " **C++** " 选项卡, 单击 "类别**预编译标头**", 然后选择 "**不使用预编译头**" 单选按钮。 单击 "确定" 关闭 "**生成设置**" 对话框。

## <a name="specifying-the-correct-object-class-name-in-the-type-library"></a>在类型库中指定正确的对象类名

使用 Visual C++服务提供的向导不正确地使用实现类名称在服务器的 ODL 文件中为可创建 OLE 的类指定 coclass。 虽然这将起作用, 但实现类名称可能不是你希望对象的用户使用的类名。 若要指定正确的名称, 请打开 ODL 文件, 找到每个 coclass 语句, 并将实现类名称替换为正确的外部名称。

请注意, 在更改 coclass 语句后, Mktyplib.exe 生成的标头文件中**CLSID**s 的变量名称将相应更改。 需要更新代码以使用新的变量名称。

## <a name="handling-exceptions-and-the-automation-error-interfaces"></a>处理异常和自动化错误接口

自动化对象的方法和属性访问器函数可能会引发异常。 如果是这样, 则应在双重接口实现中处理它们, 并通过 OLE 自动化错误处理接口`IErrorInfo`将有关异常的信息传递回控制器。 此接口通过`IDispatch`和 VTBL 接口提供详细的上下文错误信息。 若要指示错误处理程序可用, 应实现`ISupportErrorInfo`接口。

为了说明错误处理机制, 假设用于实现标准调度的 ClassWizard 生成的函数会引发异常。 MFC 的实现`IDispatch::Invoke`通常会捕获这些异常, 并将它们转换为`Invoke`通过调用返回的 EXCEPTINFO 结构。 但是, 当使用 VTBL 接口时, 您负责自行捕获异常。 作为保护双重接口方法的示例:

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

`CATCH_ALL_DUAL`发生异常时, 请注意返回正确的错误代码。 `CATCH_ALL_DUAL`使用`ICreateErrorInfo`接口将 MFC 异常转换为 OLE 自动化错误处理信息。 (Mfcdual.h 文件`CATCH_ALL_DUAL`中有一个示例宏。[ACDUAL](../overview/visual-cpp-samples.md)示例中的 H。 它调用来处理异常`DualHandleException`的函数位于文件 mfcdual.h 中。CPP。)`CATCH_ALL_DUAL`根据发生的异常类型确定要返回的错误代码:

- [COleDispatchException](../mfc/reference/coledispatchexception-class.md) -在这种情况`HRESULT`下, 使用以下代码构造:

    ```cpp
    hr = MAKE_HRESULT(SEVERITY_ERROR, FACILITY_ITF, (e->m_wCode + 0x200));
    ```

   这会创建`HRESULT`一个特定于引发异常的接口。 错误代码将由0x200 抵消, 以避免对标准 OLE 接口的系统`HRESULT`定义的任何冲突。

- [CMemoryException](../mfc/reference/cmemoryexception-class.md) -在这种情况`E_OUTOFMEMORY`下, 将返回。

- 在此情况下, `E_UNEXPECTED`将返回任何其他异常。

若要指示使用 OLE 自动化错误处理程序, 还应实现`ISupportErrorInfo`接口。

首先, 将代码添加到自动化类定义, 以显示其`ISupportErrorInfo`支持。

其次, 将代码添加到自动化类的接口映射, 以将`ISupportErrorInfo`实现类与 MFC 的`QueryInterface`机制关联起来。 语句与为`ISupportErrorInfo`定义的类匹配。 `INTERFACE_PART`

最后, 实现定义的用于支持`ISupportErrorInfo`的类。

( [ACDUAL](../overview/visual-cpp-samples.md)示例包含三个宏, 用于帮助执行这三个`DECLARE_DUAL_ERRORINFO`步骤`DUAL_ERRORINFO_PART`:、 `IMPLEMENT_DUAL_ERRORINFO`和, 它们都包含在 mfcdual.h 中。H.)

下面的示例实现一个定义为支持`ISupportErrorInfo`的类。 `CAutoClickDoc`是自动化类的名称, `IID_IDualAClick`是接口的**IID** , 它是通过 OLE 自动化 error 对象报告的错误的源:

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
