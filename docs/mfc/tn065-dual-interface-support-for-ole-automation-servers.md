---
title: "TN065： 针对 OLE 自动化服务器的双重接口支持 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.ole
dev_langs: C++
helpviewer_keywords:
- dual interfaces [MFC], OLE Automation
- TN065 [MFC]
- ACDUAL sample [MFC]
- Automation servers [MFC], dual-interface support
ms.assetid: b5c8ed09-2f7f-483c-80fc-2a47ad896063
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 959938be27e66a765ee0ae9e5aef9b3c1f1aed6f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="tn065-dual-interface-support-for-ole-automation-servers"></a>TN065：针对 OLE 自动化服务器的双重接口支持
> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 本说明介绍如何将双重接口支持添加到基于 MFC 的 OLE 自动化服务器应用程序。 [ACDUAL](../visual-cpp-samples.md)示例阐释了双重接口支持和本说明中的代码示例摘自 ACDUAL。 如本说明中所述的宏`DECLARE_DUAL_ERRORINFO`， `DUAL_ERRORINFO_PART`，和`IMPLEMENT_DUAL_ERRORINFO`、 ACDUAL 示例的一部分以及可以在 MFCDUAL 中找到。H。  
  
## <a name="dual-interfaces"></a>双重接口  
 尽管 OLE 自动化让你能够实现`IDispatch`接口、 VTBL 接口或双重接口 （其中包含同时），Microsoft 强烈建议你实现双重接口，对所有公开 OLE 自动化对象。 双重接口通过具有明显优势`IDispatch`-只有或仅 VTBL 接口：  
  
-   在编译时通过 VTBL 接口，或通过运行时绑定可以发生`IDispatch`。  
  
-   可以使用 VTBL 接口的 OLE 自动化控制器可能受益于提高性能。  
  
-   使用的现有 OLE 自动化控制器`IDispatch`接口将继续工作。  
  
-   VTBL 接口是更轻松地从 c + + 调用。  
  
-   双重接口所需的与 Visual Basic 对象支持功能的兼容性。  
  
## <a name="adding-dual-interface-support-to-a-ccmdtarget-based-class"></a>将双重接口支持添加到基于 CCmdTarget 类  
 双重接口是一个自定义派生自接口实际上只是`IDispatch`。 若要实现中的双重接口支持的最直接方式`CCmdTarget`-基于的类是第一个实现正常调度使用 MFC 和 ClassWizard，类接口，然后在以后添加自定义的接口。 大多数情况下，你自定义接口的实现会将只需委托回 MFC`IDispatch`实现。  
  
 首先，修改你的服务器定义为您的对象的双重接口的 ODL 文件。 若要定义双重接口，必须使用接口语句，而不是`DISPINTERFACE`Visual c + + 向导生成的语句。 而不是删除现有`DISPINTERFACE`语句中，添加新的接口语句。 通过保留`DISPINTERFACE`窗体中，你可以继续使用 ClassWizard 将属性和方法添加到你的对象，但必须将等效的属性和方法添加到接口语句。  
  
 双重接口的接口语句必须具有**OLEAUTOMATION**和**双重**属性和接口必须派生自`IDispatch`。 你可以使用[GUIDGEN](../visual-cpp-samples.md)示例，用于创建**IID**双重接口：  
  
```  
[ uuid(0BDD0E81-0DD7-11cf-BBA8-444553540000), // IID_IDualAClick  
    oleautomation, 
    dual 
]  
interface IDualAClick : IDispatch  
 {  
 };  
```  
  
 一旦你准备好接口语句，启动添加的方法和属性的条目。 双重接口，对于，你需要重新排列参数列表，使你的方法和双重接口中的属性访问器函数将返回`HRESULT`并将其返回值作为具有属性的参数传递`[retval,out]`。 请记住，对于属性，你将需要添加这两个读取 (`propget`) 和写入 (`propput`) 访问具有相同 id 的函数。例如:  
  
```  
[propput,
    id(1)] HRESULT text([in] BSTR newText);

[propget,
    id(1)] HRESULT text([out,
    retval] BSTR* retval);
```  
  
 定义方法和属性后，你需要组件类语句中添加对接口语句的引用。 例如:  
  
```  
[ uuid(4B115281-32F0-11cf-AC85-444553540000) ]  
coclass Document  
{  
    dispinterface IAClick;  
 [default] interface IDualAClick;  
};  
```  
  
 后已更新 ODL 文件，使用 MFC 的接口映射机制来在对象类中定义的双重接口的实现类和对应的条目中 MFC 的`QueryInterface`机制。 你需要中的一项`INTERFACE_PART`ODL，接口语句中的每个条目以及调度接口的条目的块。 与每个 ODL 条目**propput**属性需要一个名为函数`put_propertyname`。 与每个条目**propget**属性需要一个名为函数`get_propertyname`。  
  
 若要定义你的双重接口的实现类，添加`DUAL_INTERFACE_PART`到你的对象类定义的块。 例如:  
  
```  
BEGIN_DUAL_INTERFACE_PART(DualAClick,
    IDualAClick)  
    STDMETHOD(put_text)(THIS_ BSTR newText);

    STDMETHOD(get_text)(THIS_ BSTR FAR* retval);

    STDMETHOD(put_x)(THIS_ short newX);

    STDMETHOD(get_x)(THIS_ short FAR* retval);

    STDMETHOD(put_y)(THIS_ short newY);

    STDMETHOD(get_y)(THIS_ short FAR* retval);

    STDMETHOD(put_Position)(THIS_ IDualAutoClickPoint FAR* newPosition);

    STDMETHOD(get_Position)(THIS_ IDualAutoClickPoint FAR* FAR* retval);

    STDMETHOD(RefreshWindow)(THIS);

 STDMETHOD(SetAllProps)(THIS_ short x,
    short y,
    BSTR text);

    STDMETHOD(ShowWindow)(THIS);

END_DUAL_INTERFACE_PART(DualAClick) 
```  
  
 若要连接到 MFC 的双重接口[QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms687230)机制，添加`INTERFACE_PART`到接口映射的条目：  
  
```  
BEGIN_INTERFACE_MAP(CAutoClickDoc,
    CDocument)  
    INTERFACE_PART(CAutoClickDoc,
    DIID_IAClick,
    Dispatch)  
    INTERFACE_PART(CAutoClickDoc,
    IID_IDualAClick,
    DualAClick)  
END_INTERFACE_MAP()  
```  
  
 接下来，你需要填写接口的实现。 大多数情况下，你将能够将委托给现有 MFC`IDispatch`实现。 例如:  
  
```  
STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::AddRef()  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    return pThis->ExternalAddRef();

}  
STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::Release()  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    return pThis->ExternalRelease();

}  
STDMETHODIMP CAutoClickDoc::XDualAClick::QueryInterface(
    REFIID iid,
    LPVOID* ppvObj)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    return pThis->ExternalQueryInterface(&iid,
    ppvObj);

}  
STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfoCount(
    UINT FAR* pctinfo)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);

    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetTypeInfoCount(pctinfo);

}  
STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfo(
    UINT itinfo,
    LCID lcid,
    ITypeInfo FAR* FAR* pptinfo)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);

    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetTypeInfo(itinfo,
    lcid,
    pptinfo);

}  
STDMETHODIMP CAutoClickDoc::XDualAClick::GetIDsOfNames(
    REFIID riid,
    OLECHAR FAR* FAR* rgszNames,
    UINT cNames,  
    LCID lcid,
    DISPID FAR* rgdispid)   
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);

    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetIDsOfNames(riid,
    rgszNames,
    cNames,   
    lcid,
    rgdispid);

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
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);

    ASSERT(lpDispatch != NULL);

    return lpDispatch->Invoke(dispidMember,
    riid,
    lcid,  
    wFlags,
    pdispparams,
    pvarResult,  
    pexcepinfo,
    puArgErr);

}  
```  
  
 对于对象的方法和属性访问器函数，你需要填写实现。 通常，您方法和属性的函数可以委派回使用类向导生成的方法。 但是，如果将属性设置为直接访问的变量，你需要编写代码以 get/put 值到变量。 例如:  
  
```  
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick) *// MFC automatically converts from Unicode BSTR to *// Ansi CString,
    if necessary...  
    pThis->m_str = newText;  
    return NOERROR;  
}  
STDMETHODIMP CAutoClickDoc::XDualAClick::get_text(BSTR* retval)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick) *// MFC automatically converts from Ansi CString to *// Unicode BSTR,
    if necessary...  
    pThis->m_str.SetSysString(retval);

 return NOERROR;  
}  
```  
  
## <a name="passing-dual-interface-pointers"></a>传递双重接口指针  
 传递双重接口指针不简单，特别是如果你需要调用`CCmdTarget::FromIDispatch`。 `FromIDispatch`仅适用于 MFC 的`IDispatch`指针。 要解决此问题的一种方法是适用于原始查询`IDispatch`指针集由 MFC 并将该指针传递给需要它的函数。 例如:  
  
```  
STDMETHODIMP CAutoClickDoc::XDualAClick::put_Position(
    IDualAutoClickPoint FAR* newPosition)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDisp = NULL;  
    newPosition->QueryInterface(IID_IDispatch, (LPVOID*)&lpDisp);

    pThis->SetPosition(lpDisp);

 lpDisp->Release();
return NOERROR;  
}  
```  
  
 之前通过双重接口方法向回传递一个指针，你可能需要将其从 MFC 转换`IDispatch`指向双重接口指针。 例如:  
  
```  
STDMETHODIMP CAutoClickDoc::XDualAClick::get_Position(
    IDualAutoClickPoint FAR* FAR* retval)  
{  
    METHOD_PROLOGUE(CAutoClickDoc,
    DualAClick)  
    LPDISPATCH lpDisp;  
    lpDisp = pThis->GetPosition();
lpDisp->QueryInterface(IID_IDualAutoClickPoint, (LPVOID*)retval);

    return NOERROR;  
}  
```  
  
## <a name="registering-the-applications-type-library"></a>注册应用程序的类型库  
 应用程序向导不会生成代码以向系统注册 OLE 自动化服务器应用程序的类型库。 虽然有其他方法可注册类型库，很方便地将注册的类型库，当独立运行应用程序时，它正在，即更新其 OLE 类型信息，该应用程序。  
  
 注册应用程序的类型库只要运行应用程序单独存在：  
  
-   包括 AFXCTL。在你标准 H 包括标头文件，STDAFX。H，若要访问的定义`AfxOleRegisterTypeLib`函数。  
  
-   应用程序中`InitInstance`函数中，找到调用`COleObjectFactory::UpdateRegistryAll`。 此调用后添加对的调用`AfxOleRegisterTypeLib`，并指定**LIBID**对应于你的类型库，以及你的类型库的名称：  
  
 ' * / / 服务器应用程序启动时独立的它是一个不错的主意 * / / 若要在已损坏的情况下更新系统注册表。  
    m_server。UpdateRegistry(OAT_DISPATCH_OBJECT);

 COleObjectFactory::UpdateRegistryAll();* / DUAL_SUPPORT_START * / / 请确保注册类型库或双重接口将不起作用。  
AfxOleRegisterTypeLib(AfxGetInstanceHandle()，LIBID_ACDual，_T("AutoClik.TLB"));* / DUAL_SUPPORT_END  
 ```  
  
## Modifying Project Build Settings to Accommodate Type Library Changes  
 To modify a project's build settings so that a header file containing **UUID** definitions is generated by MkTypLib whenever the type library is rebuilt:  
  
1.  On the **Build** menu, click **Settings**, and then select the ODL file from the file list for each configuration.  
  
2.  Click the **OLE Types** tab and specify a filename in the **Output header** filename field. Use a filename that is not already used by your project, because MkTypLib will overwrite any existing file. Click **OK** to close the **Build Settings** dialog box.  
  
 To add the **UUID** definitions from the MkTypLib-generated header file to your project:  
  
1.  Include the MkTypLib-generated header file in your standard includes header file, STDAFX.H.  
  
2.  Create a new file, INITIIDS.CPP, and add it to your project. In this file, include your MkTypLib-generated header file after including OLE2.H and INITGUID.H:  
  
 ```  
    initIIDs.c： 定义双重接口的 Iid  
    这必须不是用预编译标头生成。  
      #<a name="include-ole2h"></a>包括 < ole2.h >  
      #<a name="include-initguidh"></a>包括 < initguid.h >  
      #<a name="include-acdualh"></a>包括"acdual.h"  
 ```  
  
3.  On the **Build** menu, click **Settings**, and then select INITIIDS.CPP from the file list for each configuration.  
  
4.  Click the **C++** tab, click category **Precompiled Headers**, and select the **Not using precompiled headers** radio button. Click OK to close the **Build Settings** dialog box.  
  
## Specifying the Correct Object Class Name in the Type Library  
 The wizards shipped with Visual C++ incorrectly use the implementation class name to specify the coclass in the server's ODL file for OLE-creatable classes. While this will work, the implementation class name is probably not the class name you want users of your object to use. To specify the correct name, open the ODL file, locate each coclass statement, and replace the implementation class name with the correct external name.  
  
 Note that when the coclass statement is changed, the variable names of **CLSID**s in the MkTypLib-generated header file will change accordingly. You will need to update your code to use the new variable names.  
  
## Handling Exceptions and the Automation Error Interfaces  
 Your automation object's methods and property accessor functions may throw exceptions. If so, you should handle them in your dual-interface implementation and pass information about the exception back to the controller through the OLE Automation error-handling interface, **IErrorInfo**. This interface provides for detailed, contextual error information through both `IDispatch` and VTBL interfaces. To indicate that an error handler is available, you should implement the **ISupportErrorInfo** interface.  
  
 To illustrate the error-handling mechanism, assume that the ClassWizard-generated functions used to implement the standard dispatch support throw exceptions. MFC's implementation of **IDispatch::Invoke** typically catches these exceptions and converts them into an EXCEPTINFO structure that is returned through the `Invoke` call. However, when VTBL interface is used, you are responsible for catching the exceptions yourself. As an example of protecting your dual-interface methods:  
  
```  
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)  
{  
    METHOD_PROLOGUE （CAutoClickDoc，DualAClick）  
    TRY_DUAL(IID_IDualAClick) {* / / MFC 会自动将转换到 Unicode BSTR 从 * / / Ansi CString，如有必要...  
    pThis-> m_str = newText;  
    返回 NOERROR;  
 }  
    CATCH_ALL_DUAL}  
```  
  
 `CATCH_ALL_DUAL` takes care of returning the correct error code when an exception occurs. `CATCH_ALL_DUAL` converts an MFC exception into OLE Automation error-handling information using the **ICreateErrorInfo** interface. (An example `CATCH_ALL_DUAL` macro is in the file MFCDUAL.H in the [ACDUAL](../visual-cpp-samples.md) sample. The function it calls to handle exceptions, `DualHandleException`, is in the file MFCDUAL.CPP.) `CATCH_ALL_DUAL` determines the error code to return based on the type of exception that occurred:  
  
- [COleDispatchException](../mfc/reference/coledispatchexception-class.md) - In this case, `HRESULT` is constructed using the following code:  
  
 ```  
    hr = MAKE_HRESULT(SEVERITY_ERROR,
    FACILITY_ITF,   
 (e-> m_wCode + 0x200));

 ```  
  
     This creates an `HRESULT` specific to the interface that caused the exception. The error code is offset by 0x200 to avoid any conflicts with system-defined `HRESULT`s for standard OLE interfaces.  
  
- [CMemoryException](../mfc/reference/cmemoryexception-class.md) - In this case, `E_OUTOFMEMORY` is returned.  
  
-   Any other exception - In this case, `E_UNEXPECTED` is returned.  
  
 To indicate that the OLE Automation error handler is used, you should also implement the **ISupportErrorInfo** interface.  
  
 First, add code to your automation class definition to show it supports **ISupportErrorInfo**.  
  
 Second, add code to your automation class's interface map to associate the **ISupportErrorInfo** implementation class with MFC's `QueryInterface` mechanism. The `INTERFACE_PART` statement matches the class defined for **ISupportErrorInfo**.  
  
 Finally, implement the class defined to support **ISupportErrorInfo**.  
  
 (The [ACDUAL](../visual-cpp-samples.md) sample contains three macros to help do these three steps, `DECLARE_DUAL_ERRORINFO`, `DUAL_ERRORINFO_PART`, and `IMPLEMENT_DUAL_ERRORINFO`, all contained in MFCDUAL.H.)  
  
 The following example implements a class defined to support **ISupportErrorInfo**. `CAutoClickDoc` is the name of your automation class and `IID_IDualAClick` is the **IID** for the interface that is the source of errors reported through the OLE Automation error object:  
  
```  
STDMETHODIMP_(ULONG) CAutoClickDoc::XSupportErrorInfo::AddRef()   
{  
    METHOD_PROLOGUE （CAutoClickDoc，SupportErrorInfo）   
    返回 pThis-> ExternalAddRef();

}   
STDMETHODIMP_(ULONG) CAutoClickDoc::XSupportErrorInfo::Release()   
{   
    METHOD_PROLOGUE （CAutoClickDoc，SupportErrorInfo）   
    返回 pThis-> ExternalRelease();

}   
STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::QueryInterface （REFIID iid，LPVOID * ppvObj）   
{   
    METHOD_PROLOGUE （CAutoClickDoc，SupportErrorInfo）   
    返回 pThis-> ExternalQueryInterface （和 iid，ppvObj）;

}   
STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::InterfaceSupportsErrorInfo (REFIID iid)   
{   
    METHOD_PROLOGUE （CAutoClickDoc，SupportErrorInfo）   
    返回 (iid = = IID_IDualAClick)，则为 S_OK: S_FALSE;   
}  
```  
  
## See Also  
 [Technical Notes by Number](../mfc/technical-notes-by-number.md)   
 [Technical Notes by Category](../mfc/technical-notes-by-category.md)

