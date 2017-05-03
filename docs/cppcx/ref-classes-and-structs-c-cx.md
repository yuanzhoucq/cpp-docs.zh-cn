---
title: "Ref 类和结构 (C++-CX) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3d736b82-0bf0-48cf-bac1-cc9d110b70d1
caps.latest.revision: 42
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 42
---
# Ref 类和结构 (C++-CX)
[!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] \([!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]\) 支持用户定义的 ref 类和 ref 结构，以及用户定义的值类和值结构。 这些数据结构是主容器，[!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 通过它们支持 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]类型系统。 根据某些特定规则将其内容发送到元数据，这将使它们可在 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]组件和用 C\+\+ 或其他语言编写的 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]应用程序之间传递。  
  
 ref 类或 ref 结构具有以下基本功能：  
  
-   它必须在一个命名空间内声明，处于命名空间范围之内，并且在该命名空间中可具有公共或私有可访问性。 仅将公共类型发送到元数据。 不允许使用嵌套公共类定义，包括嵌套公共[枚举](../cppcx/enums-c-cx.md)类。 有关更多信息，请参见[命名空间和类型可见性](../cppcx/namespaces-and-type-visibility-c-cx.md)。  
  
-   它可作为成员 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]（包括 ref 类、值类、ref 结构、值结构或可以为 null 的值结构）而包含。 它还可以包含标量类型（例如 float64、bool 等）。 它还可以包含非公共的标准 C\+\+ 类型（例如 `std::vector`）或自定义类。[!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 构造可能具有 `public`、`protected`、`internal`、`private` 或 `protected private` 可访问性。 所有 `public` 或 `protected` 成员将发送到元数据。 标准 C\+\+ 类型必须具有 `private`、`internal` 或 `protected private` 可访问性，这可阻止将该类型发送到元数据。  
  
-   它可实现一个或多个接口类或接口结构。  
  
-   它可从一个基类继承，并且基类自身具有附加限制。 公共 ref 类层次结构的继承比私有 ref 类中的继承具有更多限制。  
  
-   它不能声明为泛型。 如果它具有私有可访问性，则可以为模板。  
  
-   其生存期由自动引用计数管理。  
  
## 声明  
 下面的代码片段声明 `Person` ref 类。 请注意，标准 C\+\+ `std::map` 类型用于私有成员，[!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]`IMapView` 接口用于公共接口。 另请注意，“^”追加到引用类型的声明中。  
  
 [!code-cpp[cx_classes#03](../snippets/cpp/VS_Snippets_Misc/cx_classes/cpp/class1.h#03)]  
  
## 实现  
 此代码示例演示 `Person` ref 类的实现：  
  
 [!code-cpp[cx_classes#04](../snippets/cpp/VS_Snippets_Misc/cx_classes/cpp/class1.cpp#04)]  
  
## 用法  
 下一个代码示例演示客户端代码如何使用 `Person` ref 类。  
  
 [!code-cpp[cx_classes#05](../snippets/cpp/VS_Snippets_Misc/cx_classes/cpp/class1.cpp#05)]  
  
 也可以使用堆栈语义来声明本地 ref 类变量。 此类对象的行为类似于基于堆栈的变量，即使内存仍是动态分配的也是如此。 一个重要区别是：不能将跟踪引用 \(%\) 分配给使用堆栈语义声明的变量；这将确保引用计数在函数退出时递减为零。 此示例演示一个基本 ref 类 `Uri`，以及一个使用它与堆栈语义的函数：  
  
 [!code-cpp[cx_classes#06](../snippets/cpp/VS_Snippets_Misc/cx_classes/cpp/class1.cpp#06)]  
  
## 内存管理  
 使用 `ref new` 关键字在动态内存中分配 ref 类。  
  
 [!code-cpp[cx_classes#01](../snippets/cpp/VS_Snippets_Misc/cx_classes/cpp/class1.h#01)]  
  
 句柄到对象运算符 ^ 称为“乘幂号”，它基本上是一个 C\+\+ 智能指针。 当上个乘幂号超出范围或显式设置为 `nullptr` 时，它指向的内存将自动销毁。  
  
 按照定义，ref 类具有引用语义。 分配 ref 类变量时，句柄被复制，而非对象本身。 在下一个示例中，分配后，`myClass` 和 `myClass2` 都指向同一内存位置。  
  
 [!code-cpp[cx_classes#02](../snippets/cpp/VS_Snippets_Misc/cx_classes/cpp/class1.h#02)]  
  
 实例化 C\+\+\/CX ref 类后，在调用其构造函数之前将使用零实例化其内存；因此，无需使用零实例化单个成员，包括属性。 如果 C\+\+\/CX 类派生自 Windows 运行时 C\+\+ 库 \(WRL\) 类，将仅使用零实例化 C\+\+\/CX 派生类部分。  
  
## 成员  
 ref 类可包含 `public`、`protected` 和 `private` 函数成员；仅 `public` 和 `protected` 成员将发送到元数据。 允许嵌套类和 ref 类，但它们不能是 `public`。 不允许公共字段；必须将公共数据成员声明为属性。 私有或受保护内部数据成员可以是字段。 默认情况下，在 ref 类中，所有成员的可访问性都是 `private`。  
  
 ref 结构与 ref 类相同，只是在默认情况下，它的成员具有 `public` 可访问性。  
  
 `public` ref 类或 ref 结构是在元数据中发出的，但若要能够从其他 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]应用和 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]组件使用该类或结构，则它必须至少有一个公共或受保护的构造函数。 具有公共构造函数的公共 ref 类还必须声明为 `sealed`，以阻止通过应用程序二进制接口 \(ABI\) 进行进一步的派生。  
  
 因为 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]类型系统不支持常量，公共成员不能声明为 const。 可以使用静态属性声明一个具有常数值的公共数据成员。  
  
 定义公共 ref 类或结构时，编译器将必需的特性应用到类，并将该信息存储到应用程序的 .winmd 文件中。 但是，当你定义公共未密封的 ref 类时，手动应用 `Windows::Foundation::Metadata::WebHostHidden` 特性可确保该类对用 JavaScript 编写的 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]应用程序不可见。  
  
 ref 类可在任何 `const`、`private` 或 `internal` 成员中包含标准 C\+\+ 类型（包括 `protected private` 类型）。  
  
 不允许传递具有类型参数的公共 ref 类。 不允许用户定义的泛型 ref 类。 私有、内部或受保护的私有 ref 类可以是模板。  
  
## 析构函数  
 在 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 中，对公共析构函数调用 `delete` 会调用析构函数，无论对象的引用计数如何都是如此。 此行为能让你定义析构函数以采用确定性方式对非 RAII 资源执行自定义清理。 但是，即使在这种情况下，对象自身也不会从内存中删除。 只有当引用计数达到零时，对象的内存才会释放。  
  
 如果类的析构函数不是公共的，则仅当引用计数达到零时它才会被调用。 如果对具有私有析构函数的对象调用 `delete`，编译器会引发 C4493 警告，指出“删除表达式没有影响，因为\<类型名称\>的析构函数没有‘public’可访问性”。  
  
 Ref 类析构函数只能进行以下声明：  
  
-   公共和虚拟（在密封的或未密封的类型上允许）  
  
-   受保护的私有和非虚拟（仅在未密封的类型上允许）  
  
-   私有和非虚拟（仅在密封的类型上允许）  
  
 不允许可访问性、虚拟性和密封性的任何其他组合。  如果你未显式声明析构函数，则编译器将在类型的基类或任何成员具有公共析构函数时生成公共虚拟析构函数。 否则，编译器将针对未密封的类型生成受保护的私有非虚拟析构函数，或针对密封的类型生成私有非虚拟析构函数。  
  
 如果你尝试访问已运行其析构函数的类的成员，则此行为是未定义的；它最有可能导致程序崩溃。 对不包含公共析构函数的类型调用 `delete t` 不起作用。 对其类型层次结构中具有已知 `delete this` 或 `private` 析构函数的类型或基类调用 `protected private` 也不起作用。  
  
 在声明公共析构函数时，编译器将生成代码以便 ref 类实现 `Platform::IDisposable`，并且析构函数实现 `Dispose` 方法。`Platform::IDisposable` 是 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 的 `Windows::Foundation::IClosable` 投影。 绝不显式实现这些接口。  
  
## 继承  
 Platform::Object 是所有 ref 类的通用基类。 所有 ref 类都可以隐式转换为 Platform::Object，并且可重写 [Object::ToString](../cppcx/object-tostring-method-c-cx.md)。 但是，[!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]继承模型不是常规继承模型；在 C\+\+\/CX 中，这意味着用户定义的公共 ref 类不能用作基类。  
  
 如果创建 XAML 用户控件，并且对象参与依赖项属性系统，则可以使用 `Windows::UI::Xaml::DependencyObject` 用作基类。  
  
 在定义继承自 `MyBase` 的未密封类 `DependencyObject` 后，你的组件或应用程序中的其他公共或私有 ref 类可从 `MyBase` 继承。 应仅为支持虚拟方法重写、多态标识和封装在公共 ref 类中完成继承。  
  
 私有 ref 基类不需要从现有未密封类派生。 如果你需要一个对象层次结构来对你自己的程序结构进行建模或启用代码重用，则请使用私有或内部 ref 类，或使用标准 C\+\+ 类，后者更佳。 你可通过公共密封 ref 类包装器来公开私有对象层次结构的功能。  
  
 必须将具有 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 中的公共或受保护的构造函数的 ref 类声明为密封类。 此限制意味着，用 C\# 或 Visual Basic 等其他语言编写的类无法从用 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 编写的 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]组件中声明的类型继承。  
  
 以下是适用于 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 中的继承的基本规则：  
  
-   虽然 ref 类最多从一个 ref 基类直接继承，但它可以实现任意数量的接口。  
  
-   如果类具有公共构造函数，则必须将其声明为密封类以防止进一步派生。  
  
-   你可创建具有内部或受保护的私有构造函数的公共未密封基类，前提是该基类从现有未密封基类（如 `Windows::UI::Xaml::DependencyObject`）直接或间接派生。 不支持跨 .winmd 文件继承用户定义的 ref 类；但是，ref 类可从其他 .winmd 文件中定义的接口继承。 你只能从同一 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]组件或 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]应用程序中的用户定义的 ref 基类创建派生类。  
  
-   对于 ref 类，仅支持公共继承。  
  
     [!code-cpp[cx_classes#08](../snippets/cpp/VS_Snippets_Misc/cx_classes/cpp/class1.h#08)]  
  
 下面的示例演示如何公开派生自继承层次结构中的其他 ref 类的公共 ref 类。  
  
 [!code-cpp[cx_classes#09](../snippets/cpp/VS_Snippets_Misc/cx_classes/cpp/class1.h#09)]  
  
## 请参阅  
 [类型系统](../cppcx/type-system-c-cx.md)   
 [值类和结构](../cppcx/value-classes-and-structs-c-cx.md)   
 [Visual C\+\+ 语言参考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空间参考](../cppcx/namespaces-reference-c-cx.md)