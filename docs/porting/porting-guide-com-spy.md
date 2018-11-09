---
title: 迁移指南：COM Spy
ms.date: 11/04/2016
ms.assetid: 24aa0d52-4014-4acb-8052-f4e2e4bbc3bb
ms.openlocfilehash: 67dbcc815404c26535763239eddb176fcecf03f4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441777"
---
# <a name="porting-guide-com-spy"></a>迁移指南：COM Spy

本主题是一系列文章中的第二个主题，它演示将旧版 Visual C++ 项目升级到最新版本 Visual Studio 的过程。 本主题中的示例代码是先前使用 Visual Studio 2005 编译的代码。

## <a name="comspy"></a>COMSpy

COMSpy 是一款用于监视并记录计算机上服务组件活动的程序。 服务组件是在系统中运行的并且同一网络上的其他计算机可以使用的 COM+ 组件。 这些组件可通过“Windows 控制面板”中的“组件服务”功能来管理。

### <a name="step-1-converting-the-project-file"></a>步骤 1。 转换项目文件。
项目文件可轻松转换，并生成迁移报告。 我们可通过报告中的一些条目了解可能需要处理的问题。 下面是报告的一个问题（请注意，在本主题中有时会缩短错误消息以增加可读性，例如删除完整路径）：

```Output
ComSpyAudit\ComSpyAudit.vcproj: MSB8012: $(TargetPath) ('C:\Users\UserName\Desktop\spy\spy\ComSpyAudit\.\XP32_DEBUG\ComSpyAudit.dll') does not match the Librarian's OutputFile property value '.\XP32_DEBUG\ComSpyAudit.dll' ('C:\Users\UserName\Desktop\spy\spy\XP32_DEBUG\ComSpyAudit.dll') in project configuration 'Unicode Debug|Win32'. This may cause your project to build incorrectly. To correct this, please make sure that $(TargetPath) property value matches the value specified in %(Lib.OutputFile).
```

在升级项目时频繁出现的一个问题是，可能需要审核项目属性对话框中的“链接器 OutputFile”设置。 对于 Visual Studio 2010 之前的项目，如果将 OutputFile 设置为非标准值，则自动转换向导会在此设置中出现问题。 在这种情况下，输出文件的路径会设置为非标准的文件夹 XP32_DEBUG。 为了解有关此错误的详细信息，我们可以参考与 Visual C++ 2010 项目升级相关的[博客文章](http://blogs.msdn.com/b/vcblog/archive/2010/03/02/visual-studio-2010-c-project-upgrade-guide.aspx)，该升级涉及从 vcbuild 到 msbuild 这一重大更改。 据此信息，在创建新项目时 OutputFile 设置的默认值为 `$(OutDir)$(TargetName)$(TargetExt)`，但请不要在转换过程中如此设置，因为转换项目不可能验证确保所有内容均正确。 但是，我们尝试放入此值，看看它对 OutputFile 是否有效。  此值有效，因此可以继续操作。 如果没有特殊原因要使用非标准输出文件夹，我们建议使用标准位置。 在本例中，我们选择在迁移和升级过程中将输出位置保留为非标准位置；`$(OutDir)` 在“调试”配置中解析到 XP32_DEBUG 文件夹，而在“发布”配置中解析到 ReleaseU 文件夹。

### <a name="step-2-getting-it-to-build"></a>步骤 2。 开始生成
生成迁移项目时，会出现很多错误和警告。

由于以下编译器错误，`ComSpyCtl` 不进行编译：

```Output
atlcom.h(611): error C2664: 'HRESULT CComSpy::IPersistStreamInit_Save(LPSTREAM,BOOL,ATL::ATL_PROPMAP_ENTRY *)': cannot convert argument 3 from 'const ATL::ATL_PROPMAP_ENTRY *' to 'ATL::ATL_PROPMAP_ENTRY *'atlcom.h(611): note: Conversion loses qualifiersatlcom.h(608): note: while compiling class template member function 'HRESULT ATL::IPersistStreamInitImpl<CComSpy>::Save(LPSTREAM,BOOL)'\spy\spy\comspyctl\ccomspy.h(28): note: see reference to class template instantiation 'ATL::IPersistStreamInitImpl<CComSpy>' being compiled
```

错误对 atlcom.h 中的 `IPersistStreamInitImpl` 类引用了 `Save` 方法。

```cpp
STDMETHOD(Save)(_Inout_ LPSTREAM pStm, _In_ BOOL fClearDirty)
{
     T* pT = static_cast<T*>(this);
     ATLTRACE(atlTraceCOM, 2, _T("IPersistStreamInitImpl::Save\n"));
     return pT->IPersistStreamInit_Save(pStm, fClearDirty, T::GetPropertyMap());
}
```

问题是旧版本编译器接受的转换不再有效。 为了符合 C++ 标准，将不再允许使用以前允许的一些代码。 在此用例中，将非 const 指针传递到需要 const 指针的函数是不安全的。  解决方案是找到 `CComSpy` 类中 `IPersistStreamInit_Save` 的声明并将 const 修饰符添加到第三个参数中。

```cpp
HRESULT CComSpy::IPersistStreamInit_Save(LPSTREAM pStm, BOOL /* fClearDirty */, const ATL_PROPMAP_ENTRY* pMap)
```

对 `IPersistStreamInit_Load` 进行类似更改。

```cpp
HRESULT IPersistStreamInit_Load(LPSTREAM pStm, const ATL_PROPMAP_ENTRY* pMap);
```

下一个错误与注册相关。

```Output
error MSB3073: The command "regsvr32 /s /c "C:\Users\username\Desktop\spy\spy\ComSpyCtl\.\XP32_DEBUG\ComSpyCtl.lib"error MSB3073: echo regsvr32 exec. time > ".\XP32_DEBUG\regsvr32.trg"error MSB3073:error MSB3073: :VCEnd" exited with code 3.
```

不再需要此类后期生成注册命令。 只需删除自定义生成命令，并在链接器设置中指定为注册输出即可。

### <a name="dealing-with-warnings"></a>处理警告
项目生成以下链接器警告。

```Output
warning LNK4075: ignoring '/EDITANDCONTINUE' due to '/SAFESEH' specification
```

`/EDITANDCONTINUE` 有用时，`/SAFESEH` 编译器选项在调试模式中将不起作用，因此此处的解决方法是仅在“调试”配置中禁用 `/SAFESEH`。 要在属性对话框中执行此操作，请打开产生此错误的项目的属性对话框，首先将“配置”设置为“调试”（实际为“调试 Unicode”），然后在“链接器高级”部分中将“映像具有安全异常处理程序”属性重置为“否”(`/SAFESEH:NO`)。

编译器会警告 `PROP_ENTRY_EX` 已弃用。 这是不安全的，推荐改用 `PROP_ENTRY_TYPE_EX`。

```cpp
BEGIN_PROPERTY_MAP(CComSpy)
     PROP_ENTRY_EX( "LogFile", DISPID_LOGFILE, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_ENTRY_EX( "ShowGridLines", DISPID_GRIDLINES, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_ENTRY_EX( "Audit", DISPID_AUDIT, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_ENTRY_EX( "ColWidth", DISPID_COLWIDTH, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_PAGE(CLSID_StockFontPage)
END_PROPERTY_MAP()
```

将相应更改 ccomspy.h 中的代码，并根据需要添加 COM 类型。

```cpp
BEGIN_PROPERTY_MAP(CComSpy)
     PROP_ENTRY_TYPE_EX( "LogFile", DISPID_LOGFILE, CLSID_ComSpyPropPage, IID_IComSpy, VT_BSTR)
     PROP_ENTRY_TYPE_EX( "ShowGridLines", DISPID_GRIDLINES, CLSID_ComSpyPropPage, IID_IComSpy, VT_BOOL)
     PROP_ENTRY_TYPE_EX( "Audit", DISPID_AUDIT, CLSID_ComSpyPropPage, IID_IComSpy, VT_BOOL)
     PROP_ENTRY_TYPE_EX( "ColWidth", DISPID_COLWIDTH, CLSID_ComSpyPropPage, IID_IComSpy, VT_UINT)
     PROP_PAGE(CLSID_StockFontPage)
END_PROPERTY_MAP()
```

下面将处理最后几个警告，它们也是由更严格的编译器符合性检查引起的：

```Output
\spy\comspyctl\usersub.h(70): warning C4457: declaration of 'var' hides function parameter\spy\comspyctl\usersub.h(48): note: see declaration of 'var'\spy\comspyctl\usersub.h(94): warning C4018: '<': signed/unsigned mismatch  ComSpy.cpp\spy\comspyctl\comspy.cpp(186): warning C4457: declaration of 'bHandled' hides function parameter\spy\spy\comspyctl\comspy.cpp(177): note: see declaration of 'bHandled'
```

警告 C4018 来自此代码：

```cpp
for (i=0;i<lCount;i++)
    CoTaskMemFree(pKeys[i]);
```

问题是 `i` 声明为 `UINT` 而 `lCount` 声明为 long，因此出现有符号/无符号不匹配。 由于 `lCount` 从 `IMtsEventInfo::get_Count` 中获取值，而后者使用 long 类型且不在用户代码中，因此难以将 lCount 的类型更改为 `UINT`。 因此，我们向代码添加强制转换。 C 样式转换适合此类数字强制转换，但推荐使用 static_cast 样式。

```cpp
for (i=0;i<static_cast<UINT>(lCount);i++)
    CoTaskMemFree(pKeys[i]);
```

在以下情况下出现这些警告：在具有相同名称的参数的函数中声明了变量，从而导致可能出现代码混淆。 通过更改本地变量的名称修复了此问题。

### <a name="step-3-testing-and-debugging"></a>步骤 3。 测试和调试
测试应用的方式是：首先运行各种菜单和命令，然后关闭应用程序。 唯一要注意的问题是关闭应用时的调试断言。 问题出现在 `CWindowImpl` 的析构函数中，该函数是 `CSpyCon` 对象的基类，也是应用程序的主要 COM 组件。 atlwin.h 的以下代码中出现了断言失败。

```cpp
virtual ~CWindowImplRoot()
{
     #ifdef _DEBUG
     if(m_hWnd != NULL)// should be cleared in WindowProc
     {
          ATLTRACE(atlTraceWindowing, 0, _T("ERROR - Object deleted before window was destroyed\n"));
          ATLASSERT(FALSE);
     }
     #endif //_DEBUG
}
```

`hWnd` 通常在 `WindowProc` 函数中设置为零，但未如此设置，原因是为关闭窗口的 Windows 消息 (WM_SYSCOMMAND) 调用了自定义处理程序而非默认的 `WindowProc`。 自定义处理程序未将 `hWnd` 设置为零。 MFC 的 `CWnd` 类中的类似代码显示，正在销毁某个窗口时调用 `OnNcDestroy`；而且在 MFC 中，文档建议在重写 `CWnd::OnNcDestroy` 时，应调用基础 `NcDestroy` 以确保执行正确的清理操作，包括分离窗口处理程序和窗口（即将 `hWnd` 设置为零）。 因为 atlwin.h 旧版本中已存在同一断言代码，所以此断言可能也可在示例的原始版本中触发。

为了测试应用的功能，我们使用 ATL 项目模板创建了“服务组件”，并选择在 ATL 项目向导中添加了 COM+ 支持。 如果你从未使用过服务组件，可以轻松地创建和注册一个，并在系统或网络上提供该服务组件，以供其他应用使用。 COM Spy 应用旨在监视服务组件的活动，并以此帮助诊断。

我们添加了一个类，选择了 ATL 对象并将对象名称指定为 `Dog`。 然后在 dog.h 和 dog.cpp 中添加了实现。

```cpp
STDMETHODIMP CDog::Wag(LONG* lDuration)
{
    // TODO: Add your implementation code here
    *lDuration = 100l;
    return S_OK;
}
```

接下来，生成并注册了此应用（需要以管理员的身份运行 Visual Studio），并在 Windows 控制面板中使用“服务组件”应用程序来激活它。 我们创建了一个 C# Windows 窗体项目，将一个按钮从工具箱拖动到此窗体，并双击它进入 Click 事件处理程序。 然后添加了下列代码以实例化 `Dog` 组件。

```cpp
private void button1_Click(object sender, EventArgs e)
{
    ATLProjectLib.Dog dog1 = new ATLProjectLib.Dog();
    dog1.Wag();
}
```

这将顺畅运行，不出现任何问题，且 COM Spy 启用运行并配置为监视 `Dog` 组件，然后将出现大量显示活动的数据。

## <a name="see-also"></a>请参阅

[移植和升级：示例和案例研究](../porting/porting-and-upgrading-examples-and-case-studies.md)<br/>
[下一个示例：Spy++](../porting/porting-guide-spy-increment.md)<br/>
[上一个示例：MFC Scribble](../porting/porting-guide-mfc-scribble.md)