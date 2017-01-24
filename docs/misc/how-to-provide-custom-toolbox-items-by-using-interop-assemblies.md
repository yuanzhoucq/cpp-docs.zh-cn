---
title: "如何：通过使用互操作程序集提供自定义工具箱项 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "工具箱 [Visual Studio SDK]，使用互操作程序集添加项目"
ms.assetid: c3e8b404-7086-4e08-9d07-ab9c509963ca
caps.latest.revision: 33
caps.handback.revision: 33
manager: "douge"
---
# 如何：通过使用互操作程序集提供自定义工具箱项
> [!NOTE]
>  将自定义控件添加到工具箱建议的做法是，使用 Visual Studio 10 SDK 随附的工具箱控件模板。 保留本主题仅为实现向后兼容性，以便用于将现有控件添加到工具箱。  
>   
>  有关使用模板创建工具箱控件的详细信息，请参阅 [如何：创建使用 Windows 窗体的工具箱控件](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md) 和 [创建 WPF 工具箱控件](../Topic/Creating%20a%20WPF%20Toolbox%20Control.md)。  
  
 基于互操作程序集的 VSPackage 可以通过添加 ActiveX 控件扩展 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]“工具箱”功能。  
  
 有关标准 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 工具箱剪贴板格式的列表，请参阅[扩展工具箱](../misc/extending-the-toolbox.md)。  
  
 有关 VSPackage 如何使用 [!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)] 管理“工具箱”的信息，请参阅[管理工具箱](../misc/managing-the-toolbox.md)。  
  
 有关通过自动化操作管理“工具箱”的信息，请参阅[如何：控制工具箱](../Topic/How%20to:%20Control%20the%20Toolbox.md)。  
  
## 过程  
 添加到“工具箱”的项应实现标准的“工具箱”剪贴板格式，除非添加该项的 VSPackage 充当“工具箱”项提供程序 \- 为新的格式提供实现支持。  
  
#### 实现工具箱控件  
  
-   在非托管代码中实现的 VSPackage 提供的“工具箱”项必须实现 `IDataObject` 对象或必须是 ActiveX 控件 \- 环境可从该控件获取 `IDataObject` 对象。  
  
     有关实现 `IDataObject` 对象以便支持“工具箱”的详细信息，请参阅 <xref:System.Runtime.InteropServices.ComTypes.IDataObject>、<xref:Microsoft.VisualStudio.Shell.Interop.TBXITEMINFO> 和 <xref:System.Runtime.InteropServices.ComTypes.FORMATETC>。  
  
#### 将基于互操作程序集的控件添加到“工具箱”  
  
1.  获取以下内容的实例：  
  
    1.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>，支持将控件和节（选项卡）添加到“工具箱”并控制“工具箱”配置的其他方面。  
  
    2.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>，提供对本地化和 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 设置长久保持的支持。  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> 接口继承自 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox> 接口。<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> 不是派生自 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>，且不会实现其方法。  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> 通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> 服务上的 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> 方法获得，调用方法是使用 `SID_SVsToolbox` 的服务 ID。  
  
     接口 ID `IID_IVSToolbox2` 用于获取 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>，而接口 ID `IID_IVSToolbox3` 将返回 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>。  
  
     在下面的示例中，<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> 接口通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> 接口上的 `QueryInterface` 和 `QueryService` 与 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> 一起被获取。  
  
    ```cpp  
    extern CComModule _Module;  
    CComPtr<IVsToolbox2> srpTbx2;  
    CComPtr<IVsToolbox3> srpTbx3;  
    hr = _Module.QueryService(SID_SVsToolbox, IID_IVsToolbox2, (void**) &srpTbx2));  
    hr = srpTbx2->QueryInterface( IID_IVsToolbox3, (void **)&srpTbx3)  
    ```  
  
2.  使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> 接口的实例将选项卡（节）和控件添加到“工具箱”。  
  
     在下面的示例中，将使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2.AddTab%2A> 方法添加具有本地化名称的新选项卡。  
  
     由于此本地化名称并非不变，因此可通过对 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.SetIDOfTab%2A> 方法进行调用来设置非本地化的固定名称（在本示例中为 `L"HTML"`）。  
  
     如果已存在工具箱选项卡，`AddTab2` 将返回 E\_FAIL，在这种情况下，假设该选项卡在尝试检索固定名称之前已正确添加。  
  
     如果已成功添加选项，则基于 <xref:System.Runtime.InteropServices.ComTypes.IDataObject> 的控件将会被添加到“工具箱”；否则返回错误。  
  
    ```cpp  
    CComBSTR sbstrID;  
    hr = srpTbx2->AddTab2((WCHAR*)szwDisplayTabName, *pclsidPackage);  
    if ( hr == S_OK) {  
        sbstrID =L"HTML";  
        hr = srpTbx3->SetIDOfTab( (WCHAR*)szwDisplayTabName, sbstrID);  
    }else{  
        hr = S_OK;  
        hr = srpTbx3->GetIDOfTab( (WCHAR*)szwDisplayTabName, &sbstrID );  
  
    }  
    if ( hr = S_OK){  
        hr=srpTbx2->AddItem(tbxItem, &tinfo, bstrLabel);  
    }  
    return hr;  
    ```  
  
 除了添加到“工具箱”本身外，还可将 VSPackage 配置为“工具箱”数据提供程序并且可用于扩展对 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] IDE 的拖放支持。 这允许向“工具箱”和编辑器公开任意剪贴板格式。  
  
#### 将 VSPackage 配置为工具箱项提供程序  
  
1.  将基于互操作的 VSPackage 注册为“工具箱”项提供程序。  
  
     有关注册为“工具箱”提供程序的详细信息，请参阅[注册工具箱支持功能](../misc/registering-toolbox-support-features.md)。  
  
2.  注册为支持自定义“工具箱”剪贴板格式。  
  
     如果基于互操作的 VSPackage 支持不会实现所有标准“工具箱”剪贴板格式或实现一个自定义“工具箱”剪贴板格式的控件，则它必须：  
  
    1.  注册它们支持的工具箱剪贴板格式。 有关详细信息，请参阅[注册工具箱支持功能](../misc/registering-toolbox-support-features.md)。  
  
    2.  定义可实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider2> 接口的类。  
  
        > [!NOTE]
        >  不应在实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> 接口的类上实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider2> 接口。  
  
    3.  以编程方式通知工具箱，<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProvider2> 接口的特定实现使用等效方法（<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxDataProviderRegistry.RegisterDataProvider%2A> 或 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox.RegisterDataProvider%2A>）提供对自定义数据格式的支持。  
  
         对 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox.RegisterDataProvider%2A> 方法的调用通常在实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 方法或实现 <xref:Microsoft.VisualStudio.Shell.WindowPane.OnCreate%2A> 处理程序方法中完成，因为此时 VSPackage 变为活动的。  
  
        ```cpp  
        CComPtr<IVsToolboxDataProviderRegistry> pTB;  
        if (SUCCEEDED (hr = pServiceProvider->QueryService(SID_SVsToolboxDataProviderRegistry, IID_IVsToolboxDataProviderRegistry, (PVOID*)&pTB)) && pTB != NULL)  
        {  
            CustToolboxDataProvider* pDP = new CustToolboxDataProvider;  
            if (pDP)  
            {  
                pDP->AddRef();  
                VSCOOKIE dwDPCookie; //UNDONE: pass NULL instead of ptr to the cookie when RegisterDataProvider allows it.  
                pTB->RegisterDataProvider((IVsToolboxDataProvider*)pDP, &dwDPCookie);  
                pDP->Release();  
            }  
            else  
            {  
                hr = E_OUTOFMEMORY;  
            }  
        }  
        ```  
  
 有关标准 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]“工具箱”剪切板格式列表，请参阅[扩展工具箱](../misc/extending-the-toolbox.md).  
  
## 请参阅  
 [扩展工具箱](../misc/extending-the-toolbox.md)   
 [工具箱演练](../misc/toolbox-walkthroughs.md)   
 [注册工具箱支持功能](../misc/registering-toolbox-support-features.md)   
 [高级工具箱控件开发](../misc/advanced-toolbox-control-development.md)   
 [管理工具箱](../misc/managing-the-toolbox.md)   
 [如何：控制工具箱](../Topic/How%20to:%20Control%20the%20Toolbox.md)