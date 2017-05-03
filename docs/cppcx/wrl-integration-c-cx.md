---
title: "WRL 集成 (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3ad43894-c574-477c-ad3e-240301f381d4
caps.latest.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 9
---
# WRL 集成 (C++/CX)
可以自由混合 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 代码与 [!INCLUDE[cppwrl](../cppcx/includes/cppwrl-md.md)] \([!INCLUDE[cppwrl_short](../cppcx/includes/cppwrl-short-md.md)]\) 代码。 在同一个翻译单元中，可以使用通过 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 句柄到对象 \(`^`\) 表示法和 [!INCLUDE[cppwrl_short](../cppcx/includes/cppwrl-short-md.md)] 智能指针 \(`ComPtr<T>`\) 表示法声明的对象。 但是，必须手动处理返回值、[!INCLUDE[cppwrl_short](../cppcx/includes/cppwrl-short-md.md)] HRESULT 错误代码和 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 异常。  
  
## [!INCLUDE[cppwrl_short](../cppcx/includes/cppwrl-short-md.md)] 开发  
 有关创作和使用 [!INCLUDE[cppwrl_short](../cppcx/includes/cppwrl-short-md.md)] 组件的更多信息，请参见 [Windows 运行时 C\+\+ 模板库 \(WRL\)](~/windows/windows-runtime-cpp-template-library-wrl.md)。  
  
## 示例  
 下面的代码片段演示如何通过 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 和 [!INCLUDE[cppwrl_short](../cppcx/includes/cppwrl-short-md.md)] 使用 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 类和检查元数据文件。  
  
 该示例摘自[构建 Windows 应用商店应用论坛](http://social.msdn.microsoft.com/Forums/winappswithnativecode/thread/211ef583-db11-4e55-926b-6d9ab53dbdb4)中的一个代码片段。 此代码片段的作者提供以下免责声明和规定：  
  
1.  虽然 C\+\+ 未提供反映在 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]类型上的特定 API，但是类型的 Windows 元数据文件\(.winmd\) 完全与 CLR 元数据文件兼容。 Windows 提供新的元数据发现 API \(RoGetMetaDataFile\) 来访问特定类型的 .winmd 文件。 但是，对于 C\+\+ 开发人员而言，使用这些 API 存在一定限制，因为无法实例化类。  
  
2.  编译代码后，还需要将 Runtimeobject.lib 和 Rometadata.lib 传递到链接器。  
  
3.  此代码片段按原样呈现。 它应能正常工作，但其中可能包含错误。  
  
```  
  
#include <hstring.h> #include <cor.h> #include <rometadata.h> #include <rometadataresolution.h> #include <collection.h> namespace ABI_Isolation_Workaround { #include <inspectable.h> #include <WeakReference.h> } using namespace ABI_Isolation_Workaround; #include <wrl/client.h> using namespace Microsoft::WRL; using namespace Windows::Foundation::Collections; IVector<String^>^ GetTypeMethods(Object^); MainPage::MainPage() { InitializeComponent(); Windows::Foundation::Uri^ uri = ref new Windows::Foundation::Uri("http://buildwindows.com/"); auto methods = GetTypeMethods(uri); std::wstring strMethods; std::for_each(begin(methods), end(methods), [&strMethods](../standard-library/string.md methodName) { strMethods += methodName->Data(); strMethods += L"\n"; }); wprintf_s(L"%s\n", strMethods.c_str()); } IVector<String^>^ GetTypeMethods(Object^ instance) { HRESULT hr; HSTRING hStringClassName; hr = instance->__cli_GetRuntimeClassName(reinterpret_cast<__cli_HSTRING__**>(&hStringClassName)); // internal method name subject to change post BUILD if (FAILED(hr)) __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD String^ className = reinterpret_cast<String^>(hStringClassName); ComPtr<IMetaDataDispenserEx> metadataDispenser;ComPtr<IMetaDataImport2> metadataImport;hr = MetaDataGetDispenser(CLSID_CorMetaDataDispenser, IID_IMetaDataDispenser, (LPVOID*)metadataDispenser.GetAddressOf()); if (FAILED(hr)) __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD HSTRING hStringFileName; mdTypeDef typeDefToken; hr = RoGetMetaDataFile(hStringClassName, metadataDispenser.Get(), &hStringFileName, &metadataImport, &typeDefToken); if (FAILED(hr)) __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD String^ fileName = reinterpret_cast<String^>(hStringFileName); HCORENUM hCorEnum = 0; mdMethodDef methodDefs[2048]; ULONG countMethodDefs = sizeof(methodDefs); hr = metadataImport->EnumMethods(&hCorEnum, typeDefToken, methodDefs, countMethodDefs,  &countMethodDefs); if (FAILED(hr)) __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD wchar_t methodName[1024]; ULONG countMethodName; std::wstring strMethods; Vector<String^>^ retVal = ref new Vector<String^>(); for(int i = 0; i < countMethodDefs; ++i) { countMethodName = sizeof(methodName); hr = metadataImport->GetMethodProps(methodDefs[i], nullptr, methodName, countMethodName, &countMethodName, nullptr, nullptr, nullptr, nullptr, nullptr); if (SUCCEEDED(hr)) { methodName[ countMethodName ] = 0; retVal->Append(ref new String(methodName)); } } return retVal; }  
  
```  
  
## 请参阅  
 [与其他语言的互操作性](../cppcx/interoperating-with-other-languages-c-cx.md)