---
title: Ref 类和结构 (C + + /cli CX) |Microsoft Docs
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 3d736b82-0bf0-48cf-bac1-cc9d110b70d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ba5ce5b5cb2f55caf00ea6094cb4e14b2b08c236
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42584115"
---
# <a name="ref-classes-and-structs-ccx"></a>Ref 类和结构 (C++/CX)
C + + /cli CX 支持用户定义*ref 类*并*ref 结构*，和用户定义*值类*并*值结构*。 这些数据结构是主容器的 C + /CX 支持 Windows 运行时类型系统。 其内容发送到根据某些特定规则的元数据，这使他们能够在 Windows 运行时组件和 c + + 或其他语言编写的通用 Windows 平台应用之间传递。  
  
 ref 类或 ref 结构具有以下基本功能：  
  
-   它必须在一个命名空间内声明，处于命名空间范围之内，并且在该命名空间中可具有公共或私有可访问性。 仅将公共类型发送到元数据。 不允许使用嵌套公共类定义，包括嵌套公共 [枚举](../cppcx/enums-c-cx.md) 类。 有关详细信息，请参阅[命名空间和类型可见性](../cppcx/namespaces-and-type-visibility-c-cx.md)。  
  
-   它可能包含作为成员 C + + /cli CX 包括 ref 类、 值类、 ref 结构、 值结构或可以为 null 值结构。 它还可以包含标量类型（例如 float64、bool 等）。 它还可以包含非公共的标准 C++ 类型（例如 `std::vector` ）或自定义类。 C + + /cli CX 构造可能具有`public`， `protected`， `internal`， `private`，或`protected private`可访问性。 所有 `public` 或 `protected` 成员将发送到元数据。 标准 C++ 类型必须具有 `private`、 `internal`或 `protected private` 可访问性，这可阻止将该类型发送到元数据。  
  
-   它可实现一个或多个接口类  或接口结构 。  
  
-   它可从一个基类继承，并且基类自身具有附加限制。 公共 ref 类层次结构的继承比私有 ref 类中的继承具有更多限制。  
  
-   它不能声明为泛型。 如果它具有私有可访问性，则可以为模板。  
  
-   其生存期由自动引用计数管理。  
  
## <a name="declaration"></a>声明  
 下面的代码片段声明 `Person` ref 类。 请注意，标准 c + +`std::map`私有成员和 Windows 运行时中使用类型`IMapView`接口用于公共接口。 另请注意，“^”追加到引用类型的声明中。  
  
 [!code-cpp[cx_classes#03](../cppcx/codesnippet/CPP/classesstructs/class1.h#03)]  
  
## <a name="implementation"></a>实现  
 此代码示例演示 `Person` ref 类的实现：  
  
 [!code-cpp[cx_classes#04](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#04)]  
  
## <a name="usage"></a>用法  
 下一个代码示例演示客户端代码如何使用 `Person` ref 类。  
  
 [!code-cpp[cx_classes#05](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#05)]  
  
 也可以使用堆栈语义来声明本地 ref 类变量。 此类对象的行为类似于基于堆栈的变量，即使内存仍是动态分配的也是如此。 一个重要区别是：不能将跟踪引用 (%) 分配给使用堆栈语义声明的变量；这将确保引用计数在函数退出时递减为零。 此示例演示一个基本 ref 类 `Uri`，以及一个使用它与堆栈语义的函数：  
  
 [!code-cpp[cx_classes#06](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#06)]  
  
## <a name="memory-management"></a>内存管理  
 使用 `ref new` 关键字在动态内存中分配 ref 类。  
  
 [!code-cpp[cx_classes#01](../cppcx/codesnippet/CPP/classesstructs/class1.h#01)]  
  
 句柄到对象运算符 ^ 称为“乘幂号”，它基本上是一个 C++ 智能指针。 当上个乘幂号超出范围或显式设置为 `nullptr`时，它指向的内存将自动销毁。  
  
 按照定义，ref 类具有引用语义。 分配 ref 类变量时，句柄被复制，而非对象本身。 在下一个示例中，分配后， `myClass` 和 `myClass2` 都指向同一内存位置。  
  
 [!code-cpp[cx_classes#02](../cppcx/codesnippet/CPP/classesstructs/class1.h#02)]  
  
 实例化 C++/CX ref 类后，在调用其构造函数之前将使用零实例化其内存；因此，无需使用零实例化单个成员，包括属性。 如果 C++/CX 类派生自 Windows 运行时 C++ 库 (WRL) 类，将仅使用零实例化 C++/CX 派生类部分。  
  
### <a name="members"></a>成员  
 ref 类可包含 `public`、 `protected`和 `private` 函数成员；仅 `public` 和 `protected` 成员将发送到元数据。 允许嵌套类和 ref 类，但它们不能是 `public`。 不允许公共字段；必须将公共数据成员声明为属性。 私有或受保护内部数据成员可以是字段。 默认情况下，在 ref 类中，所有成员的可访问性都是 `private`。  
  
 ref 结构与 ref 类相同，只是在默认情况下，它的成员具有 `public` 可访问性。  
  
 一个`public`ref 类或 ref 结构通过发出的元数据，但是若要能够从其他通用 Windows 平台应用和 Windows 运行时组件必须具有至少一个公共或受保护的构造函数。 具有公共构造函数的公共 ref 类还必须声明为 `sealed` ，以阻止通过应用程序二进制接口 (ABI) 进行进一步的派生。  
  
 公共成员可能不能声明为 const 因为 Windows 运行时类型系统不支持常量。 可以使用静态属性声明一个具有常数值的公共数据成员。  
  
 定义公共 ref 类或结构时，编译器将必需的特性应用到类，并将该信息存储到应用程序的 .winmd 文件中。 但是，在定义公共未密封的 ref 类时，手动应用`Windows::Foundation::Metadata::WebHostHidden`属性，以确保类不是以 JavaScript 编写的通用 Windows 平台应用对可见。  
  
 ref 类可在任何 `const` 、 `private`或 `internal`成员中包含标准 C++ 类型（包括 `protected private` 类型）。  
  
 不允许传递具有类型参数的公共 ref 类。 不允许用户定义的泛型 ref 类。 私有、内部或受保护的私有 ref 类可以是模板。  
  
## <a name="destructors"></a>析构函数  
 在 C + + /CX 中，调用`delete`对公共析构函数调用的析构函数，而无论对象的引用计数。 此行为能让你定义析构函数以采用确定性方式对非 RAII 资源执行自定义清理。 但是，即使在这种情况下，对象自身也不会从内存中删除。 只有当引用计数达到零时，对象的内存才会释放。  
  
 如果类的析构函数不是公共的，则仅当引用计数达到零时它才会被调用。 如果您调用`delete`具有私有析构函数的对象，编译器会引发 C4493 警告，指出"删除表达式不起作用的析构函数作为\<类型名称 > 没有 'public' 可访问性。"  
  
 Ref 类析构函数只能进行以下声明：  
  
-   公共和虚拟（在密封的或未密封的类型上允许）  
  
-   受保护的私有和非虚拟（仅在未密封的类型上允许）  
  
-   私有和非虚拟（仅在密封的类型上允许）  
  
 不允许可访问性、虚拟性和密封性的任何其他组合。  如果你未显式声明析构函数，则编译器将在类型的基类或任何成员具有公共析构函数时生成公共虚拟析构函数。 否则，编译器将针对未密封的类型生成受保护的私有非虚拟析构函数，或针对密封的类型生成私有非虚拟析构函数。  
  
 如果你尝试访问已运行其析构函数的类的成员，则此行为是未定义的；它最有可能导致程序崩溃。 对不包含公共析构函数的类型调用 `delete t` 不起作用。 对其类型层次结构中具有已知 `delete this` 或 `private` 析构函数的类型或基类调用 `protected private` 也不起作用。  
  
 在声明公共析构函数时，编译器将生成代码以便 ref 类实现 `Platform::IDisposable` ，并且析构函数实现 `Dispose` 方法。 `Platform::IDisposable` 是 C + + /cli CX 投影的`Windows::Foundation::IClosable`。 绝不显式实现这些接口。  
  
## <a name="inheritance"></a>继承  
 Platform::Object 是所有 ref 类的通用基类。 所有 ref 类都可以隐式转换为 Platform::Object，并且可重写 [Object::ToString](../cppcx/platform-object-class.md#tostring)。 但是，Windows 运行时继承模型不应将用作一种通用继承模型;在 C + + /cli CX 这意味着用户定义的公共 ref 类不能用作基类。  
  
 如果创建 XAML 用户控件，并且对象参与依赖项属性系统，则可以使用 `Windows::UI::Xaml::DependencyObject` 用作基类。  
  
 在定义继承自 `MyBase` 的未密封类 `DependencyObject`后，你的组件或应用程序中的其他公共或私有 ref 类可从 `MyBase`继承。 应仅为支持虚拟方法重写、多态标识和封装在公共 ref 类中完成继承。  
  
 私有 ref 基类不需要从现有未密封类派生。 如果你需要一个对象层次结构来对你自己的程序结构进行建模或启用代码重用，则请使用私有或内部 ref 类，或使用标准 C++ 类，后者更佳。 你可通过公共密封 ref 类包装器来公开私有对象层次结构的功能。  
  
 Ref 类具有公共或受保护构造函数在 C + + /cli CX 必须声明为密封。 此限制意味着没有用 C# 或 Visual Basic 等来从您在 C + 中编写的 Windows 运行时组件中声明的类型继承其他语言编写的类的方法 + /cli CX。  
  
 下面是一些基本规则的继承在 C + + /cli CX:  
  
-   虽然 ref 类最多从一个 ref 基类直接继承，但它可以实现任意数量的接口。  
  
-   如果类具有公共构造函数，则必须将其声明为密封类以防止进一步派生。  
  
-   你可创建具有内部或受保护的私有构造函数的公共未密封基类，前提是该基类从现有未密封基类（如 `Windows::UI::Xaml::DependencyObject`）直接或间接派生。 不支持跨 .winmd 文件继承用户定义的 ref 类；但是，ref 类可从其他 .winmd 文件中定义的接口继承。 从用户定义的 ref 基类类仅在同一个 Windows 运行时组件或通用 Windows 平台应用中，可以创建派生的类。  
  
-   对于 ref 类，仅支持公共继承。  
  
     [!code-cpp[cx_classes#08](../cppcx/codesnippet/CPP/classesstructs/class1.h#08)]  
  
 下面的示例演示如何公开派生自继承层次结构中的其他 ref 类的公共 ref 类。  
  
 [!code-cpp[cx_classes#09](../cppcx/codesnippet/CPP/classesstructs/class1.h#09)]  
  
## <a name="see-also"></a>请参阅  
 [类型系统](../cppcx/type-system-c-cx.md)   
 [值类和结构](../cppcx/value-classes-and-structs-c-cx.md)   
 [Visual c + + 语言参考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空间参考](../cppcx/namespaces-reference-c-cx.md)