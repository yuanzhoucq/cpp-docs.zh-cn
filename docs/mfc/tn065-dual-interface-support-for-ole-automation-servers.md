---
title: "TN065：针对 OLE 自动化服务器的双重接口支持 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ACDUAL 示例 [MFC]"
  - "自动化服务器, 双接口支持"
  - "双重接口, OLE 自动化"
  - "TN065"
ms.assetid: b5c8ed09-2f7f-483c-80fc-2a47ad896063
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# TN065：针对 OLE 自动化服务器的双重接口支持
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。  因此，某些过程和主题可能已过时或不正确。  要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 此注释讨论如何添加双重接口支持。基于 MFC 的 OLE 自动化服务器应用程序。  [ACDUAL](../top/visual-cpp-samples.md) 示例阐释双重接口支持，因此，本批注的示例代码。ACDUAL 中采用。  此注释说明的宏，如 `DECLARE_DUAL_ERRORINFO`，`DUAL_ERRORINFO_PART`和 `IMPLEMENT_DUAL_ERRORINFO`，这些标识符是 ACDUAL 示例的一部分，可以在 MFCDUAL.H. 查找。  
  
## 双重接口  
 虽然为 OLE 自动化使您可以实现 `IDispatch` 接口或 VTBL、接口包含两个\) 的双重接口 \(Microsoft，强烈建议您实现所有公开的 OLE 自动化对象的双重接口。  双重接口具有明显的好处与单个 `IDispatch`或 VTBL 接口：  
  
-   绑定可以出现编译时通过 VTBL 接口，或在运行时使用 `IDispatch`。  
  
-   可以使用 VTBL 接口的 OLE 自动化控制器可能受益于增强的性能。  
  
-   使用 `IDispatch` 的现有的 OLE 自动化控制器将继续运行。  
  
-   VTBL 接口更便于从 C\+\+ 调用。  
  
-   双重接口的兼容所需的与 Visual Basic 对象支持功能。  
  
## 添加双重接口支持。基于 CCmdTarget 的类  
 双重接口实际上是从 `IDispatch`派生的自定义接口。  最简单的方法来在 `CCmdTarget`的双重接口支持。使用 MFC 和 ClassWizard，基类是先在类上实现的接口，然后正常调度后添加自定义接口。  在很大程度上，自定义接口实现将委托回 MFC `IDispatch` 实现。  
  
 首先，请修改服务器将 ODL 文件转换定义对象的双重接口。  若要定义双重接口，必须使用接口语句，而不是 Visual C\+\+ 向导生成的 `DISPINTERFACE` 语句。  而不是移除现有的 `DISPINTERFACE` 语句时，请添加新接口语句。  通过将 `DISPINTERFACE` 形式，可以继续使用 ClassWizard 添加属性和方法向对象，但是，您必须将的等效属性和方法添加到接口语句。  
  
 双重接口的接口语句都必须具有 **OLEAUTOMATION** 和 **DUAL** 特性，因此，必须从 `IDispatch`派生的接口。  可以使用 [GUIDGEN](../top/visual-cpp-samples.md) 示例创建双绑定接口的 **IID** :  
  
```  
[ uuid(0BDD0E81-0DD7-11cf-BBA8-444553540000), // IID_IDualAClick  
   oleautomation,  
   dual  
]  
interface IDualAClick : IDispatch  
  {  
  };  
```  
  
 一旦具有相应接口语句，请启动将方法和属性添加的项。  对于双绑定接口，您需要重新排列参数列表，方法和属性访问器函数。双重接口返回 `HRESULT` 并将其返回值作为参数的 `[retval,out]`特性。  确保对于属性，您将需要添加读取 \(`propget`和\) 编写 \(`propput`\) 使用相同 ID. 访问的功能  例如：  
  
```  
[propput, id(1)] HRESULT text([in] BSTR newText);  
[propget, id(1)] HRESULT text([out, retval] BSTR* retval);  
```  
  
 在方法和属性以后在 coclass 语句中定义，您需要向接口语句的引用。  例如：  
  
```  
[ uuid(4B115281-32F0-11cf-AC85-444553540000) ]  
coclass Document  
{  
   dispinterface IAClick;  
   [default] interface IDualAClick;  
};  
```  
  
 将 ODL 文件的更新，请使用 MFC 接口映射机制定义双重接口的实现类中对象类并在此 MFC 的 `QueryInterface` 机制的相应项。  在每一项的 `INTERFACE_PART` 块中的语句以及一项需要 ODL 接口，调度接口的项。  具有 **propput** 特性的每 ODL 输入需要一个名为 `put_propertyname`的函数。  具有 **propget** 特性的每一项需要一个名为 `get_propertyname`的函数。  
  
 若要定义双重接口的实现类中，添加一个 `DUAL_INTERFACE_PART` 块。对象类定义类。  例如：  
  
```  
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
  
 若要连接双重接口到 MFC 的 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms687230) 机制，将 `INTERFACE_PART` 项添加到接口映射：  
  
```  
BEGIN_INTERFACE_MAP(CAutoClickDoc, CDocument)  
  INTERFACE_PART(CAutoClickDoc, DIID_IAClick, Dispatch)  
  INTERFACE_PART(CAutoClickDoc, IID_IDualAClick, DualAClick)  
END_INTERFACE_MAP()  
```  
  
 接下来，需要填写接口的实现。  在很大程度上，可以委托给现有 MFC `IDispatch` 实现。  例如：  
  
```  
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
             REFIID iid, LPVOID* ppvObj)  
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
          UINT itinfo, LCID lcid, ITypeInfo FAR* FAR* pptinfo)  
{  
   METHOD_PROLOGUE(CAutoClickDoc, DualAClick)  
   LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);  
   ASSERT(lpDispatch != NULL);  
   return lpDispatch->GetTypeInfo(itinfo, lcid, pptinfo);  
}  
STDMETHODIMP CAutoClickDoc::XDualAClick::GetIDsOfNames(  
       REFIID riid, OLECHAR FAR* FAR* rgszNames, UINT cNames,  
       LCID lcid, DISPID FAR* rgdispid)   
{  
   METHOD_PROLOGUE(CAutoClickDoc, DualAClick)  
   LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);  
   ASSERT(lpDispatch != NULL);  
   return lpDispatch->GetIDsOfNames(riid, rgszNames, cNames,   
                                    lcid, rgdispid);  
}  
STDMETHODIMP CAutoClickDoc::XDualAClick::Invoke(  
    DISPID dispidMember, REFIID riid, LCID lcid, WORD wFlags,  
    DISPPARAMS FAR* pdispparams, VARIANT FAR* pvarResult,  
    EXCEPINFO FAR* pexcepinfo, UINT FAR* puArgErr)  
{  
   METHOD_PROLOGUE(CAutoClickDoc, DualAClick)  
   LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);  
   ASSERT(lpDispatch != NULL);  
   return lpDispatch->Invoke(dispidMember, riid, lcid,  
                             wFlags, pdispparams, pvarResult,  
                             pexcepinfo, puArgErr);  
}  
```  
  
 对于对象的方法和属性访问器函数，需要填写实现。  方法和属性函数委托回 ClassWizard 通常可以使用生成的方法。  但是，在中，如果您直接访问变量的属性，需要获取\/编写的代码将值放入变量。  例如：  
  
```  
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
  
## 传递双重接口指针  
 尤其是如果需要调用 `CCmdTarget::FromIDispatch`，传递双重接口指针不是直接的。  在`FromIDispatch` MFC 的 `IDispatch` 指针仅工作。  一种方式可以避免此问题将 `IDispatch` 指针的原始设置查询由 MFC 并将该指针到需要的函数。  例如：  
  
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
  
 在传递双重接口指针。方法，您可能需要将它转换从 MFC `IDispatch` 指向双重接口指针。  例如：  
  
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
  
## 注册应用程序的库类型  
 AppWizard 不生成代码向系统注册的 OLE 自动化服务器应用的类型库。  如果有其他方式注册类型库时，该应用程序注册类型库是方便的，也就是说时，该更新的 OLE 类型信息，每次运行应用程序无关。  
  
 注册应用程序的库类型，只要应用程序是独立运行的位置：  
  
-   在标准的 AFXCTL.H 包括头文件，STDAFX.H，访问 `AfxOleRegisterTypeLib` 函数定义。  
  
-   在应用程序的 `InitInstance` 函数中，找到对 `COleObjectFactory::UpdateRegistryAll`的调用。  此调用后面，添加一个调用 `AfxOleRegisterTypeLib`，指定与 **LIBID** 类型库，以及相应类型库的名称一起：  
  
    ```  
    // When a server application is launched stand-alone, it is a good idea  
    // to update the system registry in case it has been damaged.  
    m_server.UpdateRegistry(OAT_DISPATCH_OBJECT);  
    COleObjectFactory::UpdateRegistryAll();  
    // DUAL_SUPPORT_START  
    // Make sure the type library is registered or dual interface won't work.  
    AfxOleRegisterTypeLib(AfxGetInstanceHandle(), LIBID_ACDual, _T("AutoClik.TLB"));  
    // DUAL_SUPPORT_END  
    ```  
  
## 修改项目生成设置以容纳类型库更改的  
 修改项目的生成设置，以便包含 **UUID** 定义的头文件 MkTypLib 由生成的类型，只要重新生成库：  
  
1.  在 **生成** 菜单上，单击 **设置**，然后从文件列表将 ODL 文件转换每个配置。  
  
2.  单击 **OLE Types** 选项卡并在文件名 **Output header** 字段指定文件名。  使用项目尚未使用的文件名，MkTypLib，因为会覆盖任何现有文件。  单击 **确定** 关闭 **生成设置** 对话框。  
  
 从 MkTypLib 生成的头文件添加 **UUID** 定义添加到项目：  
  
1.  在标准的 MkTypLib 生成的头文件包括头文件，STDAFX.H。  
  
2.  创建新文件，INITIIDS.CPP，并将其添加到项目。  在文件、MkTypLib 包括生成的头文件后包括 OLE2.H 和 INITGUID.H:  
  
    ```  
    // initIIDs.c: defines IIDs for dual interfaces  
    // This must not be built with precompiled header.  
      #include <ole2.h>  
      #include <initguid.h>  
      #include "acdual.h"  
    ```  
  
3.  在 **生成** 菜单上，单击 **设置**，然后从文件列表中选择该 INITIIDS.CPP 每个配置。  
  
4.  单击 **C\+\+** 选项卡，单击类别 **预编译头**，然后选择 **不使用预编译头** 单选按钮。  单击"确定关闭 **生成设置** 对话框。  
  
## 指定正确的对象类名称在类型库中  
 向导随 Visual C\+\+ 为 OLE 创建类使用不当实现类名称指定 coclass。服务器将 ODL 文件转换。  当这是可行时，实现类名称可能不希望对象的用户传递给使用的类名。  若要指定正确的名称，请打开 ODL 文件，找到每个 coclass 语句，并将正确的外部名称替换实现类名称。  
  
 注意，在 coclass 语句更改，则 **CLSID**的变量的名称。MkTypLib 生成的头文件中将相应变化。  需要更新代码使用新的变量名称。  
  
## 处理异常和自动化错误接口  
 自动化对象的方法和属性访问器函数可能会引发异常。  如果是这样，则应在处理其双重接口实现和传递有关异常的信息回控制器 OLE 自动化错误接口处理，**IErrorInfo**。  此接口提供上下文，详细的错误信息通过 `IDispatch` 和 VTBL 接口。  若要指示错误处理程序可用，则应实现 **ISupportErrorInfo\(I\)** 接口。  
  
 为了说明错误处理机制，类向导用于的假定，生成的函数实现标准计划支持引发异常。  **IDispatch::Invoke** 的 MFC 实现通常捕捉这些异常和转换到通过调用 `Invoke` 返回的 EXCEPTINFO 结构。  但是，当您运行时，使用 VTBL 接口，捕获异常。  作为保护双重接口方法：  
  
```  
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
  
 在异常情况时，`CATCH_ALL_DUAL` 处理返回正确的错误代码。  使用 **ICreateErrorInfo** 接口，`CATCH_ALL_DUAL` 转换异常到 MFC OLE 自动化错误处理信息。\(示例 `CATCH_ALL_DUAL` 宏在 [ACDUAL](../top/visual-cpp-samples.md) 示例的文件 MFCDUAL.H。  它调用处理异常的 `DualHandleException`函数，MFCDUAL.CPP，在文件\)。`CATCH_ALL_DUAL` 确定错误代码以根据发生异常类型的返回：  
  
-   [COleDispatchException](../mfc/reference/coledispatchexception-class.md) \- 使用以下代码，在这种情况下，`HRESULT` 构造：  
  
    ```  
    hr = MAKE_HRESULT(SEVERITY_ERROR, FACILITY_ITF,   
                               (e->m_wCode + 0x200));  
    ```  
  
     这将创建 `HRESULT` 特定于生成异常的接口。  错误代码。0x200 偏移避免系统定义的 `HRESULT`的全部冲突标准 OLE 接口的。  
  
-   [CMemoryException](../mfc/reference/cmemoryexception-class.md) \- 在此情况下，`E_OUTOFMEMORY` 返回。  
  
-   其他异常，在此情况下为 `E_UNEXPECTED` 返回。  
  
 若要指示使用 OLE 自动化错误处理程序，则还应实现 **ISupportErrorInfo\(I\)** 接口。  
  
 首先，请将代码添加到自动化类定义其显示支持 **ISupportErrorInfo\(I\)**。  
  
 接下来，将代码添加到自动化类的接口映射实现关联 **ISupportErrorInfo\(I\)** 类使用 MFC 的 `QueryInterface` 机制。  `INTERFACE_PART` 语句与为 **ISupportErrorInfo\(I\)**定义的类。  
  
 最后，实现定义的 **ISupportErrorInfo\(I\)**类支持。  
  
 \( [ACDUAL](../top/visual-cpp-samples.md) 示例包含三宏执行这三个步骤帮助，`DECLARE_DUAL_ERRORINFO`、`DUAL_ERRORINFO_PART`和 `IMPLEMENT_DUAL_ERRORINFO`，这些都包含在 MFCDUAL.H.\)  
  
 下面的示例实现定义的类支持 **ISupportErrorInfo\(I\)**。  `CAutoClickDoc` 是实现类的名称，`IID_IDualAClick` 是通过 OLE 自动化错误对象报告错误源接口的 **IID** :  
  
```  
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
   REFIID iid, LPVOID* ppvObj)   
{   
   METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)   
   return pThis->ExternalQueryInterface(&iid, ppvObj);   
}   
STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::InterfaceSupportsErrorInfo(   
   REFIID iid)   
{   
   METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)   
   return (iid == IID_IDualAClick) ? S_OK : S_FALSE;   
}  
```  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)