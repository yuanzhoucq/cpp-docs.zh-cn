---
title: 添加成员函数
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.classes.member.function
- vc.codewiz.function.overview
helpviewer_keywords:
- member functions, adding to classes
- classes [C++], adding members
- add member function wizard [C++]
ms.assetid: 55b25ddb-541d-44ed-957c-974ef91cfc85
ms.openlocfilehash: 1cd7abbbc43ae56861b3b83451b41933b8b0b4f0
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693407"
---
# <a name="add-a-member-function"></a>添加成员函数

在“类视图”中，可以将成员函数添加到任何类中。 在执行此操作时，会将一个声明添加到标头文件中，并且会将一个存根成员函数主体添加到稍后可修改的类实现文件中。

**将成员函数添加到类：**

1. 在 **“类视图”** 中，展开项目节点，显示项目中的类。 （若要打开“类视图”，请在菜单栏上，选择“视图”、“类视图”。）

1. 打开想要向其添加成员函数的类的快捷菜单，然后选择“添加”、“添加函数”。

1. 提供有关成员函数的适当详细信息。 有关详细信息，请参阅[添加成员函数向导](#add-member-function-wizard)。

1. 选择“完成”按钮以生成成员函数代码。

## <a name="in-this-section"></a>本节内容

- [添加成员函数向导](#add-member-function-wizard)

## <a name="add-member-function-wizard"></a>添加成员函数向导

此向导将成员函数声明添加到头文件中。 此外，还将存根成员函数实现添加到所选类的实现文件中。

如果使用此向导添加了成员函数，则可在开发环境中编辑代码。

- **返回类型**

  设置要添加的成员函数的返回类型。 可自行提供返回类型，或者从可用类型列表中进行选择。 有关类型的信息，请参阅[基础类型](../cpp/fundamental-types-cpp.md)。

  | | | |
  |---|---|---|
  | `char` | `int` | `unsigned int` |
  | `double` | `long` | `unsigned long` |
  | `float` | `short` | `void` |
  | `HRESULT` | `unsigned char` | |

- **函数名**

  设置要添加的成员函数的名称。

- **参数类型**

  如果成员函数具有参数，则设置要为成员函数添加的参数的类型。 可自行提供参数类型，或者从可用类型列表中进行选择。

  | | | |
  |---|---|---|
  | `char` | `int` | `unsigned char` |
  | `double` | `long` | `unsigned int` |
  | `float` | `short` | `unsigned long` |

- **参数名称**

  如果成员函数具有参数，则设置要为成员函数添加的参数的名称。

- **参数列表**

  显示已添加到成员函数的参数列表。 要将参数添加到列表中，请在“参数类型”和“参数名称”框中提供类型和名称，然后选择“添加”。 要从列表中删除参数，请选择该参数，然后选择“删除”。

- **访问**

  设置成员函数的访问权限。 访问修饰符是一种关键字，用于指定其他类对该成员函数的访问权限。 有关指定访问权限的详细信息，请参阅[成员访问控制](../cpp/member-access-control-cpp.md)。 默认情况下，成员函数的访问级别设置为 `public`。

  - [public](../cpp/public-cpp.md)
  - [protected](../cpp/protected-cpp.md)
  - [private](../cpp/private-cpp.md)

  检查新的成员函数是静态的还是虚拟的，以及它是内联函数还是纯函数。 如果将成员函数设置为纯函数，则会选中“虚拟”复选框，且“内联”复选框不可用。 默认为非静态、非虚拟的成员函数。

  | 选项 | 描述 |
  |--------|-------------|
  | [Static](../cpp/storage-classes-cpp.md) |  指定该函数的作用类似于全局函数且可在类外调用（即使没有类实例化）。 成员函数无权访问非静态成员。 指定为 `Static` 的成员函数不能是虚拟函数。 |
  | [虚拟](../cpp/virtual-cpp.md) | 确保无论用于进行成员函数调用的表达式如何，均为对象调用正确的成员函数。 指定为 `Virtual` 的成员函数不能是静态函数。 |
  | **纯** | 指示没有为声明的虚拟成员函数提供实现。 纯函数仅可以在虚拟成员函数上指定。 包含纯虚拟成员函数（至少一个）的类被视为抽象类。 从抽象类中派生的类必须实现纯虚拟成员函数，或其自身也必须是抽象类。 |
  | [内联](../cpp/inline-functions-cpp.md) | 指示编译器将成员函数体的副本插入到每个调用成员函数的位置。 指定为“内联”的成员函数不能是纯函数。 |

- **.cpp 文件**

  设置写入存根成员函数实现的文件位置。 它默认写入到添加成员函数的类的 .cpp 文件中。 选择省略号按钮以更改文件名。 成员函数实现会添加到所选文件的内容中。

- **注释**

  在成员函数的头文件中提供注释。

- **函数签名**

  选择“完成”时，从代码中逐字显示成员函数。 无法编辑此框中的文本。 要更改成员函数，请在向导中更改相应的框。
