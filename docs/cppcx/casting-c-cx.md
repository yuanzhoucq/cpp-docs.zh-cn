---
title: 强制转换 (C++/CX)
ms.date: 06/19/2018
ms.assetid: 5247f6c7-6a0a-4021-97c9-21c868bd9455
ms.openlocfilehash: a51e02b59b2f7229193987f993edbccfb56b779d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233517"
---
# <a name="casting-ccx"></a>强制转换 (C++/CX)

四种不同的强制转换运算符适用于 Windows 运行时类型： [Static_cast 运算符](../cpp/static-cast-operator.md)、 [dynamic_cast 运算符](../cpp/dynamic-cast-operator.md)、 **safe_cast 运算符**和[reinterpret_cast 运算符](../cpp/reinterpret-cast-operator.md)。 **safe_cast** **`static_cast`** 当无法执行转换时，safe_cast 并引发异常;[Static_cast 运算符](../cpp/static-cast-operator.md)还执行编译时类型检查。 **`dynamic_cast`****`nullptr`** 如果无法转换类型，则返回。 尽管 **`reinterpret_cast`** 返回非 null 值，但它可能无效。 出于此原因，我们建议你不要使用， **`reinterpret_cast`** 除非你知道强制转换将会成功。 此外，建议不要在 c + +/CX 代码中使用 C 样式强制转换，因为它们与相同 **`reinterpret_cast`** 。

编译器和运行时也执行隐式强制转换，例如，在装箱操作中（当值类型或内置类型作为参数传递到其参数类型为 `Object^`的方法时）。 理论上，隐式强制转换不应在运行时引起异常；如果编译器无法执行隐式转换，它会在编译时引发错误。

Windows 运行时是对 COM 的抽象，它使用 HRESULT 错误代码而不是异常。 通常， [Platform::InvalidCastException](../cppcx/platform-invalidcastexception-class.md) 指示低级别 COM 错误 E_NOINTERFACE。

## <a name="static_cast"></a>static_cast

**`static_cast`** 在编译时检查，以确定两个类型之间是否有继承关系。 如果两种类型无关，强制转换会导致编译器错误。

**`static_cast`** Ref 类上的还会导致执行运行时检查。 **`static_cast`** Ref 类上的可以通过编译时验证，但仍在运行时失败; 在这种情况下 `Platform::InvalidCastException` ，将引发。 通常，你不必处理这些异常，因为它们指示的编程错误几乎都可以在开发和测试期间消除。

**`static_cast`** 如果代码显式声明两个类型之间的关系，并因此确保强制转换正常工作，请使用。

```cpp
    interface class A{};
    public ref class Class1 sealed : A { };
    // ...
    A^ obj = ref new Class1(); // Class1 is an A
    // You know obj is a Class1. The compiler verifies that this is possible, and in C++/CX a run-time check is also performed.
    Class1^ c = static_cast<Class1^>(obj);
```

## <a name="safe_cast"></a>safe_cast

**Safe_cast**运算符是 Windows 运行时的一部分。 它执行运行时类型检查，并在转换失败时引发 `Platform::InvalidCastException` 。 当运行时失败指示异常情况时，请使用**safe_cast** 。 **Safe_cast**的主要目的是帮助在开发和测试阶段确定编程错误的位置。 你不必处理异常，因为未经处理的异常自身会标识失败点。

如果代码未声明关系，但你确信可以执行强制转换，请使用 safe_cast。

```cpp
    // A and B are not related
    interface class A{};
    interface class B{};
    public ref class Class1 sealed : A, B { };
    // ...
    A^ obj = ref new Class1();

    // You know that obj’s backing type implements A and B, but
    // the compiler can’t tell this by comparing A and B. The run-time type check succeeds.
    B^ obj2 = safe_cast<B^>(obj);
```

## <a name="dynamic_cast"></a>dynamic_cast

使用 **`dynamic_cast`** 在将对象（更具体地说，是帽子）强制转换 **^** 为派生程度更高的类型时，预期目标对象有时可能是 **`nullptr`** 或转换可能会失败，并且你希望将该条件作为常规代码路径而不是异常来处理。 例如，在**空白应用（通用 Windows）** 项目模板中， `OnLaunched` xamp 中的方法使用 **`dynamic_cast`** 测试应用程序窗口是否包含内容。 如果它没有内容，则不是错误；而是一个预期状况。 `Windows::Current::Content` 是 `Windows::UI::XAML::UIElement` ，该转换是一个 `Windows::UI.XAML::Controls::Frame`，是继承层次结构中派生程度更大的类型。

```cpp
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
        // ...
    }
}
```

的另一个用途 **`dynamic_cast`** 是探测 `Object^` 以确定其是否包含装箱值类型。 在这种情况下，你尝试 `dynamic_cast<Platform::Box>` 或 `dynamic_cast<Platform::IBox>`。

## <a name="dynamic_cast-and-tracking-references-"></a>dynamic_cast 和跟踪引用 (%)

您还可以将应用于 **`dynamic_cast`** 跟踪引用，但在这种情况下，强制转换的行为类似于**safe_cast**。 它 `Platform::InvalidCastException` 在失败时引发，因为跟踪引用不能具有值 **`nullptr`** 。

## <a name="reinterpret_cast"></a>reinterpret_cast

建议你不要使用 [reinterpret_cast](../cpp/reinterpret-cast-operator.md) ，因为将不会执行编译时检查或运行时检查。 在最坏的情况下，可以在 **`reinterpret_cast`** 开发时无法检测到编程错误，并导致程序行为中出现微妙或灾难性错误。 因此，我们建议 **`reinterpret_cast`** 仅在那些必须在不相关的类型之间强制转换并且知道强制转换将会成功的罕见情况下使用。 很少使用的示例是将 Windows 运行时类型转换为其基础 ABI 类型，这意味着你要控制对象的引用计数。 为此，我们建议你使用 [ComPtr Class](../cpp/com-ptr-t-class.md) 智能指针。 否则，必须明确调用接口的版本。 下面的示例演示如何能将 ref 类强制转换为 `IInspectable*`。

```cpp
#include <wrl.h>
using namespace Microsoft::WRL;
auto winRtObject = ref new SomeWinRTType();
ComPtr<IInspectable> inspectable = reinterpret_cast<IInspectable*>(winRtObject);
// ...
```

如果使用 **`reinterpret_cast`** 从 OneWindows 运行时接口转换为另一个，则会导致对象被释放两次。 因此，仅当转换为非 C + + 组件扩展接口时，才使用此强制转换。

## <a name="abi-types"></a>ABI 类型

- ABI 类型位于 Windows SDK 的标头中。 为方便起见，这些标头按命名空间命名，例如 `windows.storage.h`。

- ABI 类型位于特殊的命名空间 ABI 中，例如 `ABI::Windows::Storage::Streams::IBuffer*`。

- Windows 运行时接口类型及其等效的 ABI 类型之间的转换始终是安全的，即 `IBuffer^` 到 `ABI::IBuffer*` 。

- 应始终将 Windows 运行时运行时类转换为 `IInspectable*` 或其默认接口（如果已知）。

- 在转换为 ABI 类型后，你拥有该类型的生存期，并且必须遵循 COM 规则。 我们建议你使用 `WRL::ComPtr` 简化 ABI 指针的生存期管理。

下表总结了可安全使用的情况 **`reinterpret_cast`** 。 在这些情况下，可安全地执行双向强制转换。

|||
|-|-|
|`HSTRING`|`String^`|
|`HSTRING*`|`String^*`|
|`IInspectable*`|`Object^`|
|`IInspectable**`|`Object^*`|
|`IInspectable-derived-type*`|`same-interface-from-winmd^`|
|`IInspectable-derived-type**`|`same-interface-from-winmd^*`|
|`IDefault-interface-of-RuntimeClass*`|`same-RefClass-from-winmd^`|
|`IDefault-interface-of-RuntimeClass**`|`same-RefClass-from-winmd^*`|

## <a name="see-also"></a>另请参阅

- [类型系统](../cppcx/type-system-c-cx.md)
- [C + +/CX 语言参考](../cppcx/visual-c-language-reference-c-cx.md)
- [命名空间引用](../cppcx/namespaces-reference-c-cx.md)
