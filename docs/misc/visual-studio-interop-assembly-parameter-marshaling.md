---
title: "Visual Studio 互操作程序集参数封送处理 | Microsoft Docs"
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
  - "Visual Studio SDK 互操作程序集疑难解答"
  - "互操作程序集, 参数封送处理"
  - "互操作程序集, 疑难解答"
ms.assetid: 89123eae-0fef-46d5-bd36-3d2a166b14e3
caps.latest.revision: 24
caps.handback.revision: 24
manager: "douge"
---
# Visual Studio 互操作程序集参数封送处理
用托管代码编写的 Vspackage 可能必须调用或由非托管 COM 代码调用。  通常，方法参数由 interop 封送拆收器转换或位置，自动。  但是，参数不能在某些情况下转换以简单方式。  在这些情况下，互操作程序集的方法原型参数用于尽可能密切地符合 COM 函数参数。  有关更多信息，请参见 [互操作封送处理](../Topic/Interop%20Marshaling.md)。  
  
## 常规建议  
  
##### 读取参考文档  
 如果启用了检测互操作性问题将读取每个方法的参考文档。  
  
 每个方法的参考文档包含三个相关部分:  
  
-   [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] COM 函数原型。  
  
-   互操作程序集方法原型。  
  
-   COM 参数和每个的简短说明的列表。  
  
##### 查找两个原型之间的差异  
 大多数互操作性问题从定义的不匹配派生之间特定类型的 COM 接口，并相同的定义输入 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 互操作程序集。  例如，请考虑在能够差异通过在个参数的 `null` \[out\] 值。  您必须位于两个原型之间的差异以及考虑其传递的数据的后果。  
  
##### 读取参数定义  
 读取参数定义。  COM 比有关组合不同数据类型的公共语言 \(CLR\)运行时不太强在单个参数的。  [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] COM 接口利用此灵活性的。  可以通过或需要一个非标准值或数据的类型，如指针参数的常数值应描述的所有参数，如下例所示在文档。  
  
### 为类型传递的对象无效 IUnknown \*\*  
 查找 \[out\] 定义为 COM 接口的类型 `void **` ，但是，定义为 `[`在 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 互操作程序集方法原型的`iid_is``]` 的参数。  
  
 在某些情况下， COM 接口生成一 `IUnknown` 对象，并且， COM 接口然后将它作为类型 `void **`。  这些接口尤其重要，因为，如果变量是在 \[out\] IDL 中定义，然后 `IUnknown` 对象引用计数。 `AddRef` 方法。  ，如果对象不正确，将处理内存泄漏发生。  
  
> [!NOTE]
>  ; 如果没有显式释放，在变量中创建的 COM \[out\] 接口和返回的 `IUnknown` 对象会导致内存泄漏它。  
  
 托管方法处理这些对象应视为 <xref:System.IntPtr> 作为指向 `IUnknown` 对象，并调用 <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> 方法获取对象。  调用方应然后将返回值强制转换为任何类型正确。  当不再需要某个对象时，调用 <xref:System.Runtime.InteropServices.Marshal.Release%2A> 释放。  
  
 以下正确调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> 方法和处理 `IUnknown` 对象的示例:  
  
```  
MyClass myclass;  
Object object;  
IntPtr pObj;  
Guid iid = Typeof(MyClass).Guid;  
int hr = windowFrame.QueryViewInterface(ref iid, out pObj);     
if (NativeMethods.Succeeded(hr))   
{  
    try   
    {  
        object = Marshal.GetObjectForIUnknown(pObj);  
        myclass = object;  
    }  
    finally   
    {  
        Marshal.Release(pObj);  
    }  
}  
else   
{  
    // error calling QueryViewInterface  
}  
```  
  
> [!NOTE]
>  以下方法识别通过 `IUnknown` 对象指针为类型 <xref:System.IntPtr>。  处理它们如本节所述。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
### 可选参数 \[out\]  
 查找已定义的参数，当数据类型 \[out\] \(`int`， `object`，等等\) COM 接口，但是，定义为数组相同的数据类型 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 互操作程序集方法原型。  
  
 某些 COM 接口，如 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>，将 \[out\] 参数标记为可选。  如果不需要对象，这些 COM 接口返回 `null` 指针作为该参数的值而不是创建 \[out\] 对象。  这是设计使然。  作为 VSPackage 中正确的行为的一部分，对于这些接口， `null` 指针，假设，并将错误不返回。  
  
 由于 CLR 不允许参数的值 \[out\] 是 `null`的一部分，通过这些接口旨在的行为在托管代码中不直接可用。  受影响的接口的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 互操作程序集方法在解决问题工作项定义相关参数旁边为数组，因为 CLR 通过 `null` 数组。  
  
 ，当 nothing 返回时，这些方法的托管实现应将 `null` 数组赋给该参数。  否则，请创建正确类型的单个元素的数组并将返回值数组中。  
  
 获取从接口的信息带可选参数的托管方法 \[out\] 接收该参数作为数组。  请检查数组的第一个元素的值。  如果不是 `null`，将第一个元素，就好像它是原始参数。  
  
### 通过在指针参数的常数  
 查找定义为 COM \[in\] 接口的指针，但是，定义为 <xref:System.IntPtr> 输入 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 互操作程序集原型方法的参数。  
  
 类似发生问题，当 COM 接口通过特定值，如 0， \-1，即 – 2，而不是对象指针。  不同 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)]， CLR 不允许常数转换为对象。  相反， [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 互操作程序集中定义参数作为 <xref:System.IntPtr> 类型。  
  
 这些方法的托管实现应利用该条件 <xref:System.IntPtr> 类具有 `int` 和创建 `void *` 的构造函数对象或整型常数的 <xref:System.IntPtr> ，根据。  
  
 接收此类型的 <xref:System.IntPtr> 参数的托管方法应使用 <xref:System.IntPtr> 类型转换运算符处理结果。  首先将 <xref:System.IntPtr> 为 `int` 并测试代码相关的整数常数。  如果值不匹配，请将其转换为所需类型的对象并继续 "。  
  
 在此操作的示例，请参见 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>。  
  
### OLE 返回作为 \[out\] 参数传递的值  
 查找具有 `retval` 返回值 COM 接口，但是，使 `int` 返回值和一个附加的数组 \[out\] 参数在 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 互操作程序集方法原型的方法。  应清楚这些方法需要特殊处理，因为 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 互操作程序集原型方法比 COM 接口方法还具有一个参数。  
  
 处理 OLE 事件的许多 COM 接口将有关 OLE 状态的信息到 `retval` 存储的调用过程返回接口的值。  而不是使用返回值，对应的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 互操作程序集方法将信息添加到数组参数存储的 \[out\] 调用的过程。  
  
 这些方法的托管实现在参数应创建类型的单个元素的数组和 \[out\] 参数相同并将其放在。  数组元素的值应与适当的 COM `retval`。  
  
 调用此类型的接口的托管方法应从数组中的第一个 \[out\] 元素。  此元素可以处理，就象它 `retval` 返回从相应的 COM 接口的值。  
  
## 请参阅  
 [Interop Marshaling](http://msdn.microsoft.com/zh-cn/a95fdb76-7c0d-409e-a77e-0349b1ea1490)   
 [互操作封送处理](../Topic/Interop%20Marshaling.md)   
 [互操作性疑难解答](../Topic/Troubleshooting%20Interoperability%20\(Visual%20Basic\).md)   
 [托管的 VSPackage](../misc/managed-vspackages.md)