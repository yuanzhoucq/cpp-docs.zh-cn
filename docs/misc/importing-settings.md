---
title: "导入设置 | Microsoft Docs"
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
  - "用户设置 [Visual Studio SDK], 使用托管包框架导入"
  - "IDE 设置, 使用托管包框架导入"
  - "IDE, 使用托管包框架导入设置"
  - "托管的框架, 导入环境设置"
ms.assetid: 943f9a5b-c5a5-45ce-a5a9-8d4c02f15577
caps.latest.revision: 23
caps.handback.revision: 23
manager: "douge"
---
# 导入设置
[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 集成开发环境 \(IDE\) 使用了可实现 <xref:Microsoft.VisualStudio.Shell.IProfileManager> 接口且已注册的类，以便支持 VSPackage 实现。 此实现用于检索 VSPackage 的状态。  
  
 由于 IDE 可实例化实现 <xref:Microsoft.VisualStudio.Shell.IProfileManager> 接口的类以支持 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 设置，因此，应在独立类中实现该 <xref:Microsoft.VisualStudio.Shell.IProfileManager> 接口。  
  
> [!NOTE]
>  未在实现 <xref:Microsoft.VisualStudio.Shell.Package> 的类中实现 <xref:Microsoft.VisualStudio.Shell.IProfileManager>。  
  
### 实现设置导出  
  
1.  声明可实现 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 设置的类。  
  
     将类声明为实现 <xref:Microsoft.VisualStudio.Shell.IProfileManager> 并为其提供 `GUID`。  
  
    > [!NOTE]
    >  此外，实现 <xref:Microsoft.VisualStudio.Shell.IProfileManager> 接口的类还必须实现 <xref:System.ComponentModel.IComponent> 接口，后者可通过从 <xref:System.ComponentModel.Component> 类派生该类完成。  
  
     例如:  
  
    ```  
    [Guid("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")]  
    internal class MyPackageProfileManager : Component, IProfileManager   
    ```  
  
2.  确保实现设置的类从磁盘检索状态数据。  
  
     此步骤可通过实现 <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> 方法执行。  
  
     将要保留的具体信息以及如何从 VSPackage 获取和封送处理该信息因 VSPackage 不同而不同。  
  
     无论此信息是否通过 VSPackage 保留，实现 <xref:Microsoft.VisualStudio.Shell.IProfileManager> 的类都必须使用提供的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> 接口从设置文件检索数据。  
  
     通常情况下（如以下示例所示），<xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> 还会验证检索的数据并更新 VSPackage 的状态。  
  
    ```vb#  
    Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
    If mySvc IsNot Nothing Then   
        Dim value As String   
        Dim myState As StateObject = mySvc.MyPackage.packageState   
        reader.ReadSettingString("PbrsShowDesc", value)   
        If value Is Nothing OrElse value = "" Then   
            reader.ReportError("Unable to Help Visibility Setting")   
        Else   
            myState.HelpVisible = Not value.Equals("0")   
        End If   
        reader.ReadSettingString("PbrsAlpha", value)   
        If value Is Nothing OrElse value = "" Then   
            reader.ReportError("Unable to Retrieve Sort Value")   
        Else   
            If Not value.Equals("0") Then   
                myState.SortState = SortState.Alphabetical   
            Else   
                myState.SortState = SortState.Categorized   
            End If   
        End If   
    End If  
    ```  
  
    ```c#  
    MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
    if (mySvc != null){  
      string value;  
      StateObject myState = mySvc.MyPackage.packageState;  
      reader.ReadSettingString("PbrsShowDesc", out value);  
      if (value == null || value == ""){  
          reader.ReportError("Unable to Help Visibility Setting");  
      }else{  
          myState.HelpVisible = !value.Equals("0");  
      }  
      reader.ReadSettingString("PbrsAlpha", out value);  
      if (value == null || value == ""){  
          reader.ReportError("Unable to Retrieve Sort Value");  
      }else{  
        if (!value.Equals("0")){  
          myState.SortState = SortState.Alphabetical;  
        }else{  
          myState.SortState = SortState.Categorized;  
        }  
      }  
    }  
    ```  
  
     实现的详细信息：  
  
    -   使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> 接口的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReportError%2A> 方法，通过 IDE 以交互的方式将错误返回给用户。  
  
        ```vb#  
        reader.ReadSettingString("PbrsAlpha", value)   
        If value Is Nothing OrElse value = "" Then   
            reader.ReportError("Unable to Retrieve Sort Value")   
        End If  
        ```  
  
        ```c#  
          reader.ReadSettingString("PbrsAlpha", out value);  
          if (value == null || value == ""){  
              reader.ReportError("Unable to Retrieve Sort Value");  
          }  
        ```  
  
    -   在实际检索存储的设置之前，实现 <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> 方法应使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReadFileVersion%2A> 方法以验证导出已存储设置的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 的版本是否受到支持。  
  
         在下面的示例中，该实现将检查设置是否由具有主要版本号 `m_supportVer` 的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 版本创建，如果不是，则会产生错误。  
  
        ```vb#  
        If pnMajor <> m_supportVer Then   
            reader.ReportError("Unsupported Version")   
        End If  
        ```  
  
        ```c#  
        if (pnMajor != m_supportVer){  
          reader.ReportError("Unsupported Version");  
        }  
        ```  
  
    -   [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 设置文件支持随机数据访问，因此读取和写入设置操作的顺序并不重要。 在下面的示例中，实现 <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> 方法中的编写器操作顺序与 <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> 方法中的读取操作顺序相反。  
  
    -   提供给 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> 接口的某个方法的 `pszSettingName` 参数的值必须唯一地标识每个保存在设置类别中的数据元素。  
  
        > [!NOTE]
        >  名称只需在实现类的范围内保持唯一，因为 IDE 使用实现设置的类的 GUID 和 `pszSettingName` 的值来标识每个保存的设置。 如果使用 `pszSettingName` 的相同值来调用超过一个 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> 方法，则设置文件中的原始值会被覆盖。  
  
3.  确保 VSPackage 状态和本地存储或缓存的设置之间的一致性。  
  
     此步骤通常在实现 <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> 方法期间执行（如下例所示）。 此步骤的详细信息特定于 VSPackage，并且可能涉及从自动化中获取 VSPackage 状态、查询 VSPackage，以及设置注册表项。  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> 方法应检索在初始化其支持的 VSPackage 期间通过 IDE 调用 <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> 方法时由 <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> 方法保存的信息。  
  
     在以下示例中，提供设置支持的类可实现 <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> 方法从而：  
  
    -   获取对 VSPackage 的已更新状态信息的访问权限。  
  
        ```vb#  
        Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
        Dim package As Package = TryCast(GetService(GetType(Package)), Package)   
        Dim rootKey As RegistryKey = package.UserRegistryRoot  
        ```  
  
        ```c#  
        MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
        Package package = GetService(typeof(Package)) as Package;  
        RegistryKey rootKey = package.UserRegistryRoot;  
        ```  
  
    -   使用该信息更新 VSPackage 的注册表设置。  
  
        ```vb#  
        If mySvc.MyPackage.packageState IsNot Nothing Then   
            Using rootKey   
                Using pbrsKey As RegistryKey = rootKey.CreateSubKey(Me.[GetType]().Name)   
                    Using pbrsKey   
                        DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).SaveState(pbrsKey)   
                    End Using   
                End Using   
            End Using   
        End If  
        ```  
  
        ```c#  
        if (mySvc.MyPackage.packageState != null) {  
          using (rootKey) {  
            using(RegistryKey pbrsKey = rootKey.CreateSubKey(this.GetType().Name)) {  
              using (pbrsKey) {  
                ((IComPropertyBrowser)mySvc.MyPackage.packageState).SaveState(pbrsKey);  
              }  
            }  
          }  
        }  
        ```  
  
    -   > [!NOTE]
        >  <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> 和 <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> 方法之间的工作划分取决于实现，并且从某种程度上而言比较随意。 例如，可以使用 <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> 方法的空实现以及在 <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> 方法中执行的所有注册表和状态查询来重写该实现。  
  
4.  向 VSPackage 提供支持时注册实现设置的类。  
  
     将 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 的实例（通过使用可实现 <xref:Microsoft.VisualStudio.Shell.IProfileManager> 的类的 <xref:System.Type> 而构造）应用到 VSPackage 的 <xref:Microsoft.VisualStudio.Shell.Package> 实现。  
  
    ```vb#  
    <ProvideProfile(GetType(MyPackageProfileManager), "CoreUI", "MyPackage", 1004, 1004, False)> _   
    <Guid("YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY")> _   
    Class MyPackage   
        Inherits Package   
    End Class  
    ```  
  
    ```c#  
     [ProvideProfile(typeof(MyPackageProfileManager), "CoreUI", "MyPackage", 1004, 1004, false)]  
    [Guid("YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY")]  
    class MyPackage: Package   
    ```  
  
     在此示例中，该特性告知 IDE，`MyPackageProfileManager` 类提供了对 `MyPackage` 类的设置实现。 注册表中的自定义设置点在 HKLM\\Software\\Microsoft\\VisualStudio\\*\<Version\>*\\UserSettings\\ CoreUI\_MyPackage 下进行创建，其中 *\<Version\>* 是 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 的版本，例如 8.0。  
  
     有关详细信息，请参见[用户设置的的支持](../Topic/Support%20for%20User%20Settings.md)和<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>  
  
## 示例  
 下例实现了某个类上的 <xref:Microsoft.VisualStudio.Shell.IProfileManager>。  
  
```vb#  
Imports System   
Imports System.Runtime.InteropServices   
Imports Microsoft.VisualStudio.Shell   
Imports Microsoft.VisualStudio.Shell.Interop   
Imports Microsoft.Win32   
Imports myPackageNameSpace   
Namespace myProfileManagerNameSpace  
  
    <Guid("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")> _   
    Friend Class MyPackageProfileManager   
        Inherits System.ComponentModel.Component   
        Implements IProfileManager   
        Friend Const m_supportVer As Integer = 8   
        Public Sub SaveSettingsToXml(ByVal writer As IVsSettingsWriter)   
            Dim mySvc As MyPackageService = TryCast(GetService(GetType(MyPackage)), MyPackageService)   
            If mySvc IsNot Nothing Then   
                ' Information is stored in a StateObject.   
                Dim myState As StateObject = mySvc.MyPackage.packageState   
                writer.WriteSettingString("PbrsAlpha", (If(myState.SortState = SortState.Alphabetical, "1", "0")))   
                writer.WriteSettingString("PbrsShowDesc", (If(myState.HelpVisible, "1", "0")))   
            End If   
        End Sub   
  
        Public Sub LoadSettingsFromXml(ByVal reader As IVsSettingsReader)   
  
            Dim pnMajor As Integer, pnMinor As Integer, pnBuild As Integer   
            ' First check if we are getting data from the correct major version.   
            reader.ReadVersion(pnMajor, pnMinor, pnBuild)   
            If pnMajor <> m_supportVer Then   
                reader.ReportError("Unsupported Version")   
            Else   
                Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
                If mySvc IsNot Nothing Then   
                    Dim value As String   
                    Dim myState As StateObject = mySvc.MyPackage.packageState   
                    reader.ReadSettingString("PbrsShowDesc", value)   
                    ' Not all values must be present.   
                    If value Is Nothing OrElse value = "" Then   
                        reader.ReportError("Unable to Help Visibility Setting")   
                    Else   
                        myState.HelpVisible = Not value.Equals("0")   
                    End If   
                    reader.ReadSettingString("PbrsAlpha", value)   
                    ' Not all values must be present.   
                    If value Is Nothing OrElse value = "" Then   
                        reader.ReportError("Unable to Retrieve Sort Value")   
                    Else   
                        If Not value.Equals("0") Then   
                            myState.SortState = SortState.Alphabetical   
                        Else   
                            myState.SortState = SortState.Categorized   
                        End If   
                    End If   
                End If   
            End If   
        End Sub   
  
        Public Sub SaveSettingsToStorage()   
            Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
            Dim package As Package = TryCast(GetService(GetType(Package)), Package)   
            Dim rootKey As RegistryKey = package.UserRegistryRoot   
  
            If mySvc.MyPackage.packageState IsNot Nothing Then   
                Using rootKey   
                    Using pbrsKey As RegistryKey = rootKey.CreateSubKey(Me.[GetType]().Name)   
                        Using pbrsKey   
                            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).SaveState(pbrsKey)   
                        End Using   
                    End Using   
                End Using   
            End If   
        End Sub   
  
        Public Sub LoadSettingsFromStorage()   
            Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
            Dim package As Package = TryCast(GetService(GetType(Package)), Package)   
            Dim rootKey As RegistryKey = package.UserRegistryRoot   
            Using rootKey   
                Dim pbrsKey As RegistryKey = rootKey.OpenSubKey(Me.[GetType]().Name)   
                If pbrsKey IsNot Nothing Then   
                    Using pbrsKey   
                        If mySvc.MyPackage.MakeCurrentSettingTheDefault() Then   
                            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).SaveState(pbrsKey)   
                        Else   
                            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).LoadState(pbrsKey)   
                        End If   
                    End Using   
                End If   
            End Using   
        End Sub   
    End Class   
End Namespace  
  
```  
  
```c#  
namespace myProfileManagerNameSpace  {  
  
  using System;  
  using System.Runtime.InteropServices;  
  using Microsoft.VisualStudio.Shell;  
  using Microsoft.VisualStudio.Shell.Interop;  
  using Microsoft.Win32;  
  using myPackageNameSpace;  
  
  [Guid("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")]  
  internal class MyPackageProfileManager : System.ComponentModel.Component , IProfileManager {  
    internal const int m_supportVer = 8;  
    public void SaveSettingsToXml(IVsSettingsWriter writer) {  
      MyPackageService mySvc = GetService(typeof(MyPackage)) as MyPackageService;  
      if (mySvc != null) {  
        // Information is stored in a StateObject.  
        StateObject myState = mySvc.MyPackage.packageState;  
        writer.WriteSettingString(   
                                  "PbrsAlpha",   
                                  (myState.SortState == SortState.Alphabetical ? "1" : "0"));  
        writer.WriteSettingString(   
                                  "PbrsShowDesc",   
                                  (myState.HelpVisible ? "1" : "0"));  
      }  
    }  
  
    public void LoadSettingsFromXml(IVsSettingsReader reader)  
    {  
  
      int pnMajor, pnMinor, pnBuild;  
      // First check if we are getting data from the correct major version.   
      reader.ReadVersion(pnMajor, pnMinor, pnBuild);  
      if (pnMajor != m_supportVer){  
        reader.ReportError("Unsupported Version");  
      }else{  
        MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
        if (mySvc != null){  
          string value;  
          StateObject myState = mySvc.MyPackage.packageState;  
          reader.ReadSettingString("PbrsShowDesc", out value);  
          // Not all values must be present.  
          if (value == null || value == ""){  
              reader.ReportError("Unable to Help Visibility Setting");  
          }else{  
            myState.HelpVisible = !value.Equals("0");  
          }  
          reader.ReadSettingString("PbrsAlpha", out value);  
          // Not all values must be present.  
          if (value == null || value == ""){  
              reader.ReportError("Unable to Retrieve Sort Value");  
          }else{  
            if (!value.Equals("0")){  
              myState.SortState = SortState.Alphabetical;  
            }else{  
              myState.SortState = SortState.Categorized;  
            }  
          }  
        }  
      }  
    }  
  
    public void SaveSettingsToStorage() {  
      MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
      Package package = GetService(typeof(Package)) as Package;  
      RegistryKey rootKey = package.UserRegistryRoot;  
  
      if (mySvc.MyPackage.packageState != null) {  
        using (rootKey) {  
          using(RegistryKey pbrsKey = rootKey.CreateSubKey(this.GetType().Name)) {  
            using (pbrsKey) {  
              ((IComPropertyBrowser)mySvc.MyPackage.packageState).SaveState(pbrsKey);  
            }  
          }  
        }  
      }  
    }  
  
    public void LoadSettingsFromStorage() {  
      MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
      Package package = GetService(typeof(Package)) as Package;  
      RegistryKey rootKey = package.UserRegistryRoot;  
      using (rootKey) {  
        RegistryKey pbrsKey = rootKey.OpenSubKey(this.GetType().Name);  
        if (pbrsKey != null) {  
          using (pbrsKey) {  
            if (mySvc.MyPackage.MakeCurrentSettingTheDefault()){  
              ((IComPropertyBrowser)mySvc.MyPackage.packageState).SaveState(pbrsKey);  
            }else{  
              ((IComPropertyBrowser)mySvc.MyPackage.packageState).LoadState(pbrsKey);  
            }  
          }  
        }  
      }  
    }  
  }  
}  
```  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.Shell.IProfileManager>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>   
 [导出设置](../misc/exporting-settings.md)   
 [用户设置的的支持](../Topic/Support%20for%20User%20Settings.md)