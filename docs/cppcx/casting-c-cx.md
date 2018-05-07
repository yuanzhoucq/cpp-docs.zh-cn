---
title: 强制转换 (C + + /cli CX) |Microsoft 文档
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 5247f6c7-6a0a-4021-97c9-21c868bd9455
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8f71be537ecc0dc0cb58a3ada13612dbe8cbd7d3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="casting-ccx"></a>强制转换 (C++/CX)
有四种不同的强制转换运算符适用于 Windows 运行时类型： [static_cast 运算符](../cpp/static-cast-operator.md)， [dynamic_cast 运算符](../cpp/dynamic-cast-operator.md)， **safe_cast 运算符**，和[reinterpret_cast 运算符](../cpp/reinterpret-cast-operator.md)。 当无法执行转换时，`safe_cast` 和 `static_cast` 将引发异常； [static_cast 运算符](../cpp/static-cast-operator.md) 还执行编译时类型检查。 如果`dynamic_cast` 无法转换类型，它将返回 `nullptr` 。 即使 `reinterpret_cast` 返回一个非 null 值，它也可能是无效的。 为此，我们建议不使用 `reinterpret_cast` ，除非已知该强制转换将会成功。 此外，我们建议，你不使用 C 样式强制转换中你的 C + + /cli CX 代码，因为它们是相同`reinterpret_cast`。  
  
 编译器和运行时也执行隐式强制转换，例如，在装箱操作中（当值类型或内置类型作为参数传递到其参数类型为 `Object^`的方法时）。 理论上，隐式强制转换不应在运行时引起异常；如果编译器无法执行隐式转换，它会在编译时引发错误。  
  
Windows 运行时是上 COM，它使用 HRESULT 错误代码而不是异常的抽象。 通常， [Platform::InvalidCastException](../cppcx/platform-invalidcastexception-class.md) 指示低级别 COM 错误 E_NOINTERFACE。  
  
## <a name="staticcast"></a>static_cast  
 `static_cast` 在编译时被检查，用以确定两种类型之间是否有继承关系。 如果两种类型无关，强制转换会导致编译器错误。  
  
 ref 类上的 `static_cast` 还会导致执行运行时检查。 ref 类上的 `static_cast` 可以通过编译时验证，但仍在运行时失败；在这种情况下，将引发 `Platform::InvalidCastException` 。 通常，你不必处理这些异常，因为它们指示的编程错误几乎都可以在开发和测试期间消除。  
  
 如果代码显式声明两个类型之间的关系，因此可确保能够执行强制转换，请使用 `static_cast` 。  
  
```
    interface class A{};  
    public ref class Class1 sealed : A { };  
...  
    A^ obj = ref new Class1(); // Class1 is an A  
    // You know obj is a Class1. The compiler verifies that this is possible, and in C++/CX a run-time check is also performed.  
    Class1^ c = static_cast<Class1^>(obj);
```  
  
## <a name="safecast"></a>safe_cast  
 `safe_cast`运算符是一部分 ofWindows 运行时。 它执行运行时类型检查，并在转换失败时引发 `Platform::InvalidCastException` 。 当运行时失败指示一个异常情况时，请使用 `safe_cast` 。 `safe_cast` 的主要目的是帮助在开发和测试阶段发生编程错误之处标识该错误。 你不必处理异常，因为未经处理的异常自身会标识失败点。  
  
 如果代码未声明关系，但你确信可以执行强制转换，请使用 safe_cast。  
  
```  
    // A and B are not related  
    interface class A{};  
    interface class B{};  
    public ref class Class1 sealed : A, B { };  
...  
    A^ obj = ref new Class1();  
  
    // You know that obj’s backing type implements A and B, but  
    // the compiler can’t tell this by comparing A and B. The run-time type check succeeds.  
    B^ obj2 = safe_cast<B^>(obj);  
```  
  
## <a name="dynamiccast"></a>dynamic_cast  
 使用`dynamic_cast`当强制转换对象 (更具体地说，帽子`^`) 为派生程度更大的类型，你预期目标对象可能有时是`nullptr`或者该强制转换可能失败，并且你想要作为普通的代码该条件处理路径而不是异常。 例如，在**空白应用 (通用 Windows)** 项目模板，`OnLaunched`中的方法`app.xamp.cpp`使用`dynamic_cast`来测试应用程序窗口是否包含内容。 如果它没有内容，则不是错误；而是一个预期状况。 `Windows::Current::Content` 是 `Windows::UI::XAML::UIElement` ，该转换是一个 `Windows::UI.XAML::Controls::Frame`，是继承层次结构中派生程度更大的类型。  
```
void App::OnLaunched(Windows::ApplicationModel::Activation::LaunchActivatedEventArgs^ args)  
{  
    auto rootFrame = dynamic_cast<Frame^>(Window::Current->Content);  
  
    // Do not repeat app initialization when the window already has content,  
    // just ensure that the window is active  
    if (rootFrame == nullptr)  
    {  
        // Create a Frame to act as the navigation context and associate it with  
        // a SuspensionManager key  
        rootFrame = ref new Frame();  
...  
```  
 `dynamic_cast` 的另一个使用是探测 `Object^` 以确定其是否包含装箱值类型。 在这种情况下，你尝试 `dynamic_cast<Platform::Box>` 或 `dynamic_cast<Platform::IBox>`。  
  
 **dynamic_cast 和跟踪引用 (%)**  
  
 还可以将 `dynamic_cast` 应用于跟踪引用，但在这种情况下，该强制转换的行为类似于 `safe_cast`。 它在失败时引发 `Platform::InvalidCastException` ，因为跟踪引用不能有值 `nullptr`。  
  
## <a name="reinterpretcast"></a>reinterpret_cast  
 建议你不要使用 [reinterpret_cast](../cpp/reinterpret-cast-operator.md) ，因为将不会执行编译时检查或运行时检查。 在最差的情况下， `reinterpret_cast` 有可能导致在开发期间漏掉编程错误，进而导致程序行为出现细微或致命的错误。 因此，我们建议你仅在极少情况下（即，当你必须在不相关的类型之间强制转换，而你知道该强制转换会成功时）才使用 `reinterpret_cast` 。 很少使用的一个示例是要将部分运行时类型转换为其基础 ABI 类型-这意味着，你控制着的引用计数对象。 为此，我们建议你使用 [ComPtr Class](../cpp/com-ptr-t-class.md) 智能指针。 否则，必须明确调用接口的版本。 下面的示例演示如何能将 ref 类强制转换为 `IInspectable*`。  
  
```  
#include <wrl.h>  
using namespace Microsoft::WRL;  
auto winRtObject = ref new SomeWinRTType();  
ComPtr<IInspectable> inspectable = reinterpret_cast<IInspectable*>(winRtObject);  
...
```  
  
 如果你使用`reinterpret_cast`要从 oneWindows 运行时接口转换为另一个，则会导致对象释放两次。 因此，只有当你转换为非[!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] 接口时，才使用此强制转换。  
  
 **ABI 类型**  
  
-   ABI 类型位于 Windows SDK 的标头中。 为方便起见，这些标头按命名空间命名，例如 `windows.storage.h`。  
  
-   ABI 类型位于特殊的命名空间 ABI 中，例如 `ABI::Windows::Storage::Streams::IBuffer*`。  
  
-   部分运行时接口类型和其等效的 ABI 类型之间的转换始终是安全-即，`IBuffer^`到`ABI::IBuffer*`。  
  
-   部分运行时运行时类应始终将转换为`IInspectable*`或其默认接口，如果已知。  
  
-   在转换为 ABI 类型后，你拥有该类型的生存期，并且必须遵循 COM 规则。 我们建议你使用 `WRL::ComPtr` 简化 ABI 指针的生存期管理。  
  
 下表总结了可安全使用 `reinterpret_cast`的情况。 在这些情况下，可安全地执行双向强制转换。  
  
|||  
|-|-|  
|HSTRING|String^|  
|HSTRING*|String^*|  
|IInspectable*|Object^|  
|IInspectable**|Object^*|  
|IInspectable-derived-type*|same-interface-from-winmd^|  
|IInspectable-derived-type**|same-interface-from-winmd^*|  
|IDefault-interface-of-RuntimeClass*|same-RefClass-from-winmd^|  
|IDefault-interface-of-RuntimeClass**|same-RefClass-from-winmd^*|  
  
## <a name="see-also"></a>请参阅  
 [类型系统](../cppcx/type-system-c-cx.md)   
 [Visual c + + 语言参考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空间参考](../cppcx/namespaces-reference-c-cx.md)
