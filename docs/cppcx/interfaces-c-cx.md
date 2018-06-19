---
title: 接口 (C + + /cli CX) |Microsoft 文档
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 11034314-d54a-426d-923b-5ab7a6b9f8ce
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6be3b207f6bd64685f7ec1d3f6d2271ec3b83f17
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090638"
---
# <a name="interfaces-ccx"></a>接口 (C++/CX)
虽然一个 ref 类最多从一个具体基类继承，它可以实现任意数量的接口类。 一个接口类（或接口结构）自身可继承（或需要）多个接口类、可重载其成员函数，也可具有类型参数。  
  
## <a name="characteristics"></a>特征  
 接口具有以下特征：  
  
-   接口类（或结构）必须在命名空间内声明且可具有公共或私有可访问性。 仅将公共接口发送到元数据。  
  
-   接口的成员可以包括属性、方法和事件。  
  
-   所有接口成员既是隐式公开的又是虚拟的。  
  
-   不允许字段和静态成员。  
  
-   用作属性、 方法参数或返回值只能为 Windows 运行时类型; 的类型这包括基本类型和枚举类类型。  
  
## <a name="declaration-and-usage"></a>声明和用法  
 下面的示例显示了如何声明接口。 请注意，接口可以声明为类或结构类型。  
  
 [!code-cpp[cx_interfaces#01](../cppcx/codesnippet/CPP/interfacestest/class1.h#01)]  
  
 若要实现接口，ref 类或 ref 结构会声明并实现虚方法和属性。 接口和实现 ref 类必须使用相同的方法参数名称，如以下示例所示：  
  
 [!code-cpp[cx_interfaces#02](../cppcx/codesnippet/CPP/interfacestest/class1.h#02)]  
  
## <a name="interface-inheritance-hierarchies"></a>接口继承层次结构  
 一个接口可从一个或多个接口继承。 但与 ref 类或 ref 结构不同，接口不声明继承的接口成员。 如果接口 B 从接口 A 继承，而 ref 类 C 从 B 继承，则 C 必须同时实现 A 和 B。下一示例对此进行了演示。  
  
 [!code-cpp[cx_interfaces#03](../cppcx/codesnippet/CPP/interfacestest/class1.h#03)]  
  
## <a name="implementing-interface-properties-and-events"></a>实现接口属性和事件  
 如上例所示，你可以使用普通虚拟属性实现接口属性。 你还可以在实现类中提供自定义 getter 和 setter。  在接口属性中，getter 和 setter 都必须是公共的。  
  
 [!code-cpp[cx_interfaces#04](../cppcx/codesnippet/CPP/interfacestest/class1.h#04)]  
  
 如果接口声明仅有 getter 或仅有 setter 的属性，则实现类应显式提供 getter 或 setter。  
  
 [!code-cpp[cx_interfaces#05](../cppcx/codesnippet/CPP/interfacestest/class1.h#05)]  
  
 还可以在实现类中为事件实现自定义添加和移除方法。  
  
## <a name="explicit-interface-implementation"></a>显式接口实现  
 在 ref 类实现多个接口，且这些接口具有与编译器相同的名称和签名的方法时，可以使用以下语法显式指示类方法正在实现的接口方法。  
  
 [!code-cpp[cx_interfaces#06](../cppcx/codesnippet/CPP/interfacestest/class1.h#06)]  
  
## <a name="generic-interfaces"></a>泛型接口  
 在 C + + /cli CX，`generic`关键字用于表示 Windows 运行时参数化类型。 参数化类型在元数据中发出，且可由用支持类型参数的任何语言编写的代码使用。 Windows 运行时定义几个泛型接口 — 例如， [Windows::Foundation::Collections::IVector\<T >](Windows::Foundation::Collections::IVector)-但它不支持创建公共用户定义的泛型接口中 C + + /cli CX。 但可以创建私有泛型接口。  
  
 下面是如何使用 Windows 运行时类型创作泛型接口：  
  
-   不允许将组件中的泛型用户定义的 `interface class` 发送到其 Windows 元数据文件；因此，它无法具有公共可访问性，并且其他 .winmd 文件中的客户端代码无法实现它。 它可由同一组件中的非公共 ref 类实现。 公共 ref 类可将泛型接口类型作为私有成员。  
  
     下面的代码片段演示如何声明泛型 `interface class` ，然后在私有 ref 类中实现它，并且在公共 ref 类中将该 ref 类用作私有成员。  
  
     [!code-cpp[cx_interfaces#07](../cppcx/codesnippet/CPP/interfacestest/class1.h#07)]  
  
-   泛型接口必须遵循控制可访问性、成员、  需要关系、基类等内容的标准接口规则。  
  
-   泛型接口可以采用前面带有 `typename` 或 `class`的一个或多个泛型类型参数。 不支持非类型参数。  
  
-   类型参数可以是任何 Windows 运行时类型。 即，类型参数可以是引用类型、值类型、接口类、委托、基本类型或公共枚举类。  
  
-    封闭式泛型接口是从泛型接口继承的接口，并对所有类型形参指定具体的类型实参。 它可以在可使用非泛型私有接口的任意位置使用。  
  
-    开放式泛型接口是具有一个或多个尚未为其提供具体类型的类型参数的接口。 它可以在可使用类型的任意位置使用，包括用作另一个泛型接口的类型参数。  
  
-   可以只参数化整个接口，而不是单个方法。  
  
-   不能约束类型参数。  
  
-   封闭式泛型接口具有隐式生成的 UUID。 用户不能指定 UUID。  
  
-   在接口中，对当前接口的任何引用（在方法参数、返回值或属性中）都假定引用当前实例化。 例如， *IMyIntf*意味着*IMyIntf\<T >*。  
  
-   当方法参数的类型是类型参数时，该参数或变量的声明将使用类型参数的名称，而不带任何指针、本机引用或句柄声明符。 换言之，绝不会写入“T^”。  
  
-   模板化的 ref 类必须是私有的。 它们可以实现泛型接口，并且可以将模板形参传递*T*给泛型实参*T*。模板化 ref 类的每个实例化本身都是一个 ref 类。  
  
## <a name="see-also"></a>请参阅  
 [类型系统](../cppcx/type-system-c-cx.md)   
 [Visual c + + 语言参考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空间参考](../cppcx/namespaces-reference-c-cx.md)