---
title: 委托 (C++/CX)
ms.date: 01/22/2017
ms.assetid: 3175bf1c-86d8-4eda-8d8f-c5b6753d8e38
ms.openlocfilehash: 8153ac6ffc48b43fc218ee786cdb3f64504d825e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635235"
---
# <a name="delegates-ccx"></a>委托 (C++/CX)

`delegate`关键字用于声明 Windows 运行时等效于标准 c + + 中的函数对象的引用类型。 委托声明类似于函数声明；它指定被包装的函数必须具有的返回类型和参数类型。 以下是用户定义的委托声明：

```cpp
public delegate void PrimeFoundHandler(int result);
```

委托常与事件一起使用。 事件具有委托类型，这与类具有接口类型大体相同。 委托相当于事件处理程序必须履行的协定。 以下是一个事件类成员，其类型为之前定义的委托：

```cpp
event PrimeFoundHandler^ primeFoundEvent;
```

当声明跨 Windows 运行时应用程序二进制接口向客户端将公开的委托，使用[Windows::Foundation::TypedEventHandler\<，TResult >](https://msdn.microsoft.com/library/windows/apps/br225997.aspx)。 此委托已预定义代理和存根二进制文件，使其可以由 Javascript 客户端使用。

## <a name="consuming-delegates"></a>使用委托

创建通用 Windows 平台应用时，通常使用作为 Windows 运行时类公开的事件类型的委托。 若要订阅事件，请通过指定匹配委托签名的函数或 lambda 创建其委托类型的一个实例。 然后使用 `+=` 运算符将委托对象传递到类上的事件成员。 这称为“订阅事件”。 当类实例“触发”事件时，你的函数随同由你的对象或其他对象添加的任何其他处理程序一起被调用。

> [!TIP]
> 在创建事件处理程序时，Visual Studio 可为你进行大量工作。 例如，如果你在 XAML 标记中指定事件处理程序，则将出现工具提示。 如果选择工具提示，则 Visual Studio 将自动创建事件处理程序方法并将其与发布类中的事件关联。

下面的示例演示了基本模式。 `Windows::Foundation::TypedEventHandler` 是委托类型。 处理程序函数是使用命名函数创建的。

在 app.h 中：

[!code-cpp[cx_delegates#120](../cppcx/codesnippet/CPP/delegatesevents/class1.h#120)]

在 app.cpp 中：

[!code-cpp[cx_delegates#121](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#121)]

> [!WARNING]
> 通常，对于事件处理程序，除非要格外注意以避免循环引用，否则更好的做法是使用命名函数而不是 lambda。 命名函数会通过弱引用捕获“this”指针，而 lambda 通过强引用捕获该指针并创建一个循环引用。 有关详细信息，请参阅[弱引用和中断循环](../cppcx/weak-references-and-breaking-cycles-c-cx.md)。

按照约定，由 Windows 运行时定义的事件处理程序委托名采用以下格式 * 事件处理程序 — 例如，RoutedEventHandler、 SizeChangedEventHandler 或 SuspendingEventHandler。 同样按照约定，事件处理程序委托具有两个参数并返回 void。 在没有类型参数的委托中，第一个参数的类型为 [Platform::Object^](../cppcx/platform-object-class.md)，它保持对发送方即触发事件的对象的引用。 在事件处理程序方法中使用该参数前，必须转换回原始类型。 在具有类型参数的事件处理程序委托中，第一个类型参数指定发送方的类型，第二个参数是保持事件相关信息的 ref 类的句柄。 按照约定，该类名为\*EventArgs。 例如，RoutedEventHandler 委托具有类型为 RoutedEventArgs^ 的第二个参数，DragEventHander 具有类型为 DragEventArgs^ 的第二个参数。

按照约定，包装在异步操作完成时执行的代码的委托名为 *CompletedHandler。 这些委托定义为类而不是事件的属性。 因此，不使用 `+=` 运算符订阅它们；只是将委托对象分配给属性。

> [!TIP]
> C++ IntelliSense 不显示完整委托签名，因此，它不能帮助你确定 EventArgs 参数的特定类型。 若要查找类型，可以转到 **“对象浏览器”** 查看委托的 `Invoke` 方法。

## <a name="creating-custom-delegates"></a>创建自定义委托

您可以定义自己的委托，以定义事件处理程序，或使使用者能够将自定义功能传递给 Windows 运行时组件。 像任何其他 Windows 运行时类型，公共委托不能声明为泛型。

### <a name="declaration"></a>声明

委托的声明类似函数声明，只不过委托是一种类型。 通常在命名空间范围声明委托，不过，也可以将委托声明嵌套在类声明中。 以下委托封装任何将 `ContactInfo^` 作为输入的函数并返回 `Platform::String^`。

[!code-cpp[cx_delegates#111](../cppcx/codesnippet/CPP/delegatesevents/class1.h#111)]

在声明委托类型后，可以声明该类型的类成员，或者声明以该类型的对象为参数的方法。 方法或函数也能返回委托类型。 在下面的示例中， `ToCustomString` 方法采用委托作为输入参数。 该方法使客户端代码能够提供一个从 `ContactInfo` 对象的部分或全部公共属性构造一个字符串的自定义函数。

[!code-cpp[Cx_delegates#112](../cppcx/codesnippet/CPP/delegatesevents/class1.h#112)]

> [!NOTE]
> 使用"^"符号引用委托类型时，就像你确实与任何 Windows 运行时引用类型。

事件声明始终有一个委托类型。 此示例演示一个典型的委托类型签名 Windows 运行时中：

[!code-cpp[cx_delegates#122](../cppcx/codesnippet/CPP/delegatesevents/class1.h#122)]

`Click` 类中的 `Windows:: UI::Xaml::Controls::Primitives::ButtonBase` 事件属于 `RoutedEventHandler`类型。 有关更多信息，请参见 [Events](../cppcx/events-c-cx.md)。

客户端代码首先使用 `ref new` 并提供与委托签名兼容的 lambda 来构造一个委托实例，并定义自定义行为。

[!code-cpp[Cx_delegates#113](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#113)]

然后，它调用成员函数并传递委托。 假定 `ci` 是一个 `ContactInfo^` 实例， `textBlock` 是一个 XAML `TextBlock^`。

[!code-cpp[Cx_delegates#114](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#114)]

在下一步的示例中，客户端应用程序自定义将委托传递给执行针对每个项中的委托的 Windows 运行时组件中的公共方法`Vector`:

[!code-cpp[Cx_delegates#118](../cppcx/codesnippet/CPP/clientapp/mainpage.xaml.cpp#118)]

[!code-cpp[Cx_delegates#119](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#119)]

### <a name="construction"></a>构造

可以从下列任何对象构造委托：

- lambda

- 静态函数

- 指向成员的指针

- std::function

下面的示例演示如何从各个对象构造委托。 无论用于构造对象的类型是什么，都采用完全相同的方式使用委托。

[!code-cpp[Cx_delegates#115](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#115)]

> [!WARNING]
> 如果使用捕获“this”指针的 lambda，请确保在退出该 lambda 之前使用 `-=` 运算符显式从事件中取消注册。 有关详细信息，请参阅[事件](../cppcx/events-c-cx.md)。

### <a name="generic-delegates"></a>泛型委托

在 C++/CX 中，泛型委托与泛型类声明具有类似的限制。 它们不能声明为公共委托。 你可以声明一个私有或内部泛型委托，然后通过 C++ 来使用它，但 .NET 或 JavaScript 客户端不能使用该委托，因为它没有被发出到 .winmd 元数据中。 下面的示例声明了一个只能通过 C++ 使用的泛型委托：

[!code-cpp[Cx_delegates#116](../cppcx/codesnippet/CPP/delegatesevents/class1.h#116)]

下一个示例在类定义中声明了一个专用的委托实例：

[!code-cpp[Cx_delegates#117](../cppcx/codesnippet/CPP/delegatesevents/class1.h#117)]

## <a name="delegates-and-threads"></a>委托和线程

委托和函数对象一样，包含将在未来某个时刻执行的代码。 如果创建和传递委托的代码和接受并执行委托的函数在同一线程上运行，则情况就相对简单。 如果该线程是 UI 线程，则委托可以直接操作用户界面对象（如 XAML 控件）。

如果客户端应用程序加载在一个线程的单元运行，并将委托提供给该组件的 Windows 运行时组件，则默认情况下调用委托直接在 STA 线程上。 大多数 Windows 运行时组件可以在 STA 或 MTA 中运行。

如果执行委托的代码在不同线程（如在 concurrency::task 对象的上下文中）运行，则你将负责同步对共享数据的访问。 例如，如果委托中包含对某个向量的引用，而 XAML 控件也具有对这一向量的引用，则你必须采取措施，避免因委托和 XAML 控件同时尝试访问该向量而可能发生的死锁或争用现象。 你还必须注意，在调用委托前，委托不会通过引用来尝试捕获可能超出范围的本地变量。

如果你希望在与创建委托相同的线程上回调委托，例如，将它传递给在 MTA 单元中运行的组件，并希望在和创建器相同的线程上调用它，则使用采用第二个 `CallbackContext` 参数的委托构造函数重载。 只在具有注册代理/存根的委托上使用此重载，并非所有在 Windows.winmd 中定义的委托都会注册。

如果你熟悉 .NET 中的事件处理程序，就会知道建议做法是在激发事件之前创建事件的本地副本。 这样可以避免事件处理程序在调用事件之前被移除，尽管这种情况并不常见。 在 C++/CX 中则不必如此，因为在添加或移除事件处理程序时，将创建一个新的处理程序列表。 有一个 C++ 对象会在事件被调用之前增加处理程序列表上的引用计数，因而可以保证所有处理程序都有效。 但是，这也意味着，如果将事件处理程序从使用它的线程中移除，而发布对象仍在操作其现已过期的列表副本，则仍可能调用该处理程序。 发布对象只有在下次激发事件时才能获得更新的列表。

## <a name="see-also"></a>请参阅

[类型系统](../cppcx/type-system-c-cx.md)<br/>
[Visual c + + 语言参考](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[命名空间参考](../cppcx/namespaces-reference-c-cx.md)