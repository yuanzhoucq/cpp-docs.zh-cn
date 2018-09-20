---
title: 强制转换表示法和介绍 safe_cast&lt; &gt; |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- casting
- C-style casts and /clr, motivation for new cast notation
- safe_cast keyword [C++]
ms.assetid: 4eb1d000-3b93-4394-a37b-8b8563f8dc4d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 88e8165bde08b65b4f078c4b48863c2088132fca
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427857"
---
# <a name="cast-notation-and-introduction-of-safecastltgt"></a>强制转换表示法和 safe_cast 简介&lt;&gt;

强制转换表示法已从托管扩展中的 c + + 更改为 Visual c + +。

修改现有的结构是比编写初始结构不同且更加困难的体验。 有更少的自由度，并且解决方案倾向于考虑理想重组和什么是可行的情况下提供现有的结构依赖关系。

语言扩展是另一个示例。 早在 90 年代早期面向对象的编程变得重要模式，如 c + + 中的类型安全向下转换设施的需求变得非常迫切。 向下转换为基类指针或引用的指针的指针或派生类的引用的用户显式转换。 向下转换要求显式强制转换。 基类指针的实际类型是运行时; 的一个方面的原因是编译器因此不能检查它。 或者，换句话说，向下转换功能，就像虚拟函数调用中，需要某种形式的动态解析。 这会引发两个问题：

- 为什么应向下转换为有必要在面向对象模式？ 不足的虚函数机制？ 也就是说，为什么不能声明任何需要向下转换 （或任何种类的强制转换） 是设计失败的？

- 为什么应支持的向下转换为 c + + 中的问题？ 毕竟，它不是如 Smalltalk 面向对象语言中的问题 (或随后，Java 和 C#)？ 什么是它了解使得支持向下转换功能如此困难的 c + +？

虚函数表示一系列类型的一种常见类型依赖于算法。 （我们不考虑的接口，ISO c + + 中不支持但 CLR 编程中可用，它代表了一种有趣的设计替代方法）。 已声明的公共接口 （虚函数） 和一组具体派生类表示在应用程序中的实际类型系列的抽象基类的类层次结构通常表示该系列的设计域。

一个`Light`层次结构中的计算机生成图像 (CGI) 应用程序域，例如，将具有公共属性，例如`color`， `intensity`， `position`， `on`， `off`，依次类推。 一个可以控制多个光源，而无需担心特定指示灯是否聚焦、 定向光、 非定向光 （如阳光） 或可能是靶门 light 中使用的公共接口。 在这种情况下，向下转换为特定的光的类型来实现其虚拟接口是不必要的。 但是，在生产环境中，速度是重要的。 一个可能向下转换，显式调用每个方法如果这样做内联执行调用的可执行而不是使用虚拟的机制。

因此，向下转换 c + + 中的一个原因是避免虚拟机制，从而显著提高在运行时性能。 （请注意，此手动优化自动化研究的活跃领域。 但是，很难解决比更换显式使用`register`或`inline`关键字。)

向下转换现在不在多态性双重特性到第二个原因。 可以看作是多形性的一种方法能够划分为一对被动和动态的窗体。

虚调用 （和向下转换功能） 表示的多形性的动态用法： 一个执行基于处执行程序中的特定实例的基类指针的实际类型的操作。

但是，派生的类对象分配给它的基类指针，是一种多态性; 的被动形式作为传输机制，它利用多态性。 这是主要使用`Object`，例如，预泛型 CLR 编程中。 当使用被动，基类指针通常选择传输和存储提供了过于抽象的接口。 `Object`例如，提供了大约五种方法通过其接口;任何更具体的行为需要显式向下转换。 例如，如果我们想要调整我们聚焦的角度或衰减速率，我们必须向下转换显式。 中的一系列子类型的虚拟接口实际上不可能成为其多个子级的所有可能的方法的一个超集，因此向下转换功能将始终需要一种面向对象语言中。

如果向下转换的安全功能需要在面向对象语言中，然后为什么需要多 c + + 很长时间中添加一个？ 问题是如何提供有关指针的运行时类型信息中。 在虚函数的情况下运行时信息是在中设置两个部分由编译器：

- 此类对象包含一个附加的虚拟表指针成员 (在开头或末尾类的对象; 的历史十分有趣本身)，它解决了相应的虚拟表。 例如，聚焦对象地址聚焦虚拟表、 定向光、 方向的轻型虚拟表等

- 每个虚函数有一个关联的固定在表中，槽，要调用的实际实例由存储在表中的地址。 例如，虚拟`Light`析构函数可能与槽 0 中，关联`Color`与槽 1 中，依次类推。 这是不够灵活高效的策略，因为它在编译时设置和系统开销较小。

此问题，然后，是如何提供类型信息的指针而无需更改的 c + + 指针的大小，通过添加第二个地址或通过直接添加某种形式的编码类型。 这不是对这些程序员 （和程序） 可接受的决定不使用面向对象的范例的仍然是主要的用户社区。 另一种可能是引入多态类类型的特殊指针，但这会令人费解，并使其难以混合两者，尤其是对于指针算术的问题。 它也不会维护将每个指针与其当前关联的类型和动态更新相关联的运行时表可接受。

问题就是有两个具有不同但合法的编程要求用户群体。 该解决方案必须考虑这两个群体，从而使每个其个设想不仅能够进行互操作。 这意味着，任何一侧所提供的解决方案可能是不可行，最终实现的解决方案要小于完美。 实际解决需要考虑的是多态类的定义： 多态类是包含虚拟函数。 多态类支持动态类型安全向下转换。 这解决了维护--指针-作为-地址问题，因为所有多态类都包含到其关联的虚拟表的附加指针成员。 关联的类型信息，因此，可以存储在一个扩展的虚拟表结构。 类型安全的向下转换的成本 （几乎） 已本地化为设施的用户。

类型安全的向下转换中的下一个问题是它的语法。 因为它是强制转换，为 ISO c + + 委员会原始方案使用的未修饰的强制转换语法，如本例所示：

```
spot = ( SpotLight* ) plight;
```

但是，这被拒绝委员会，因为它不允许用户控制的强制转换的成本。 如果动态类型安全向下转换具有相同的语法为以前不安全，但静态强制转换表示法，则它将成为一种替代物，并且用户已取消的运行时开销不必要和成本可能过高时不能。

一般情况下，在 c + +，没有始终要禁止显示编译器支持功能的机制。 例如，我们可以关闭虚拟机制通过使用类范围运算符 (`Box::rotate(angle)`) 或通过调用虚拟方法通过类对象 （而不是指针或引用该类的）。 这后一种取消不必需的语言，但实现问题，类似于在窗体的声明中的临时构造的禁止显示的质量：

```
// compilers are free to optimize away the temporary
X x = X::X( 10 );
```

因此以进行进一步的考虑，建议被退回和考虑了几个备用的表示法，并将恢复为该委员会是窗体 (`?type`)，这表示它的不确定性的即动态特性。 这使得用户能够切换两种形式的静态或动态的但没有人与其太高兴。 因此，它是返回到从头开始。 第三个成功的表示法是现在标准`dynamic_cast<type>`，它被推广到四个新样式强制转换表示法的一组。

在 ISO c + +`dynamic_cast`将返回`0`时应用于不适当的指针类型，并引发`std::bad_cast`异常时应用于引用类型。 在 c + + 托管扩展应用`dynamic_cast`对托管的引用类型 （由于其指针表示形式） 始终返回`0`。 `__try_cast<type>` 引入了一个模拟作为异常抛出的变体`dynamic_cast`，只不过它将引发`System::InvalidCastException`如果转换失败。

```
public __gc class ItemVerb;
public __gc class ItemVerbCollection {
public:
   ItemVerb *EnsureVerbArray() [] {
      return __try_cast<ItemVerb *[]>
         (verbList->ToArray(__typeof(ItemVerb *)));
   }
};
```

在新语法中，`__try_cast`已将转换为`safe_cast`。 下面是相同的代码段中的新语法：

```
public ref class ItemVerb;
public ref class ItemVerbCollection {
public:
   array<ItemVerb^>^ EnsureVerbArray() {
      return safe_cast<array<ItemVerb^>^>
         ( verbList->ToArray( ItemVerb::typeid ));
   }
};
```

在托管领域中，它非常重要，以便通过限制编程人员能够以使代码不可验证的方式的类型之间强制转换为可验证代码。 这是由新语法的动态编程范例的一个重要方面。 出于此原因，旧样式强制转换的实例会重新强制转换在内部为运行时强制转换，因此，例如：

```
// internally recast into the
// equivalent safe_cast expression above
( array<ItemVerb^>^ ) verbList->ToArray( ItemVerb::typeid );
```

但是，由于多态性提供主动和被动模式，因此它，有时需要执行向下转换只是为了获取子类型的非虚拟 api 的访问权限。 发生这种情况，例如，使用类的成员，要解决任何类型层次结构 （作为传输机制被动多态性） 中，但为已知特定的程序上下文中的实际实例。 在这种情况下，通过该强制转换的运行时检查将无法接受的开销。 如果新的语法是作为编程语言的托管系统，它必须提供几种可编译时 (即，静态) 向下转换。 这就是为什么应用程序的`static_cast`允许保持编译时向下转换表示法：

```
// ok: cast performed at compile-time.
// No run-time check for type correctness
static_cast< array<ItemVerb^>^>(verbList->ToArray(ItemVerb::typeid));
```

问题是没有办法保证执行程序员`static_cast`是正确和善意; 也就是说，没有方法来强制执行托管的代码可验证。 这是一个显得更为紧迫的问题的情况下动态程序比在纯模式、 但不足够编程静态和运行时强制转换之间进行切换的功能的语言不允许用户在系统中。

存在但是是性能陷阱和新语法中的缺陷。 在本机编程中，没有旧样式强制转换表示法和新样式之间没有性能差异`static_cast`表示法。 但在新语法中，旧样式强制转换表示法的新样式的使用比贵很多`static_cast`表示法。 原因是编译器在内部转换的转换会引发异常的运行时检查的旧样式表示法使用。 此外，它也会更改代码的执行配置文件会导致未捕获的异常将降低应用程序-可能是这样做是明智的但相同的错误不会导致该异常如果因为`static_cast`使用表示法。 有人可能会说这将促使用户使用新样式表示法。 而只时失败;否则，它将导致使用旧样式表示法来运行速度显著变慢而无需有一个可见的原因，了解程序类似于以下 C 程序员缺陷：

```
// pitfall # 1:
// initialization can remove a temporary class object,
// assignment cannot
Matrix m;
m = another_matrix;

// pitfall # 2: declaration of class objects far from their use
Matrix m( 2000, 2000 ), n( 2000, 2000 );
if ( ! mumble ) return;
```

## <a name="see-also"></a>请参阅

[常规语言更改 (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)<br/>
[C 样式强制转换和 /clr (C + + CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)<br/>
[safe_cast](../windows/safe-cast-cpp-component-extensions.md)