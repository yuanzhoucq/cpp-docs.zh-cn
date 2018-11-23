---
title: 添加一般 C++ 类
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.classes.adding.generic
- vc.codewiz.class.generic
helpviewer_keywords:
- Visual C++, classes
- generic classes, adding
- generic classes
- generic C++ class wizard [C++]
ms.assetid: e95a5a14-dbed-4edc-8551-344fe48613cb
ms.openlocfilehash: 08ebe572da605e0f6d4d712bd7e48159598ba844
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694135"
---
# <a name="add-a-generic-c-class"></a>添加一般 C++ 类

可以使用类视图添加一般 C++ 类。 一般 C++ 类是一种你定义的类或从你定义的类中派生的类。

**向项目添加一般 C++ 类：**

1. 在“类视图”中，右键单击要向其添加新类的项目，依次选择“添加”和“类”。

1. 在[添加类](../ide/add-class-dialog-box.md)对话框的“模板”窗格中，选择“C++ 类”。 选择“添加”以显示[一般 C++ 类向导](#generic-c-class-wizard)。

1. 在向导中，提供类名称，然后定义设置或接受默认值。

1. 若要关闭向导并查看项目中新的一般 C++ 类，请选择“完成”。

## <a name="in-this-section"></a>本节内容

- [一般 C++ 类向导](#generic-c-class-wizard)

## <a name="generic-c-class-wizard"></a>一般 C++ 类向导

将一般 C++ 类向导添加到项目。 该类不从 ATL 或 MFC 继承。

- **类名**

  设置新类的名称。

- **.h 文件**

  为新类的头文件设置名称。 默认情况下，此名称基于你在“类名”中提供的名称。 要将头文件保存至所选位置，或将类声明追加到现有文件，请选择省略号按钮 (...)。如果指定现有文件，并选择“完成”，向导会提示你指定是否要将该类声明追加至文件的内容中。 要追加该声明，请选择“是”；要返回至向导并指定另一个文件名，请选择“否”。

- **.cpp 文件**

  为新类的实现文件设置名称。 默认情况下，此名称基于你在“类名”中提供的名称。 要将该实现文件保存至所选位置，或将类声明追加到现有文件，请选择省略号按钮 (...)。如果指定现有文件，并选择“完成”，向导会提示你指定是否要将该类定义追加至文件的内容中。 要追加该定义，请选择“是”；要返回至向导并指定另一个文件名，请选择“否”。

- **基类**

  为新类设置基类。

- **访问**

  为新类的基类成员设置访问权限。 访问修饰符是一种关键字，用于指定其他类对该类成员函数的访问权限级别。 有关如何指定访问权限的详细信息，请参阅[成员访问控制](../cpp/member-access-control-cpp.md)。 默认情况下，类访问级别设置为 `public`。

  - `public`
  - `protected`
  - `private`
  - 默认（不生成访问修饰符）

- **虚拟析构函数**

  指定是否类析构函数是否为虚拟。 使用虚拟析构函数有助于确保删除派生类实例时，调用正确的析构函数。

- **内联**

  生成类构造函数和类定义作为头文件中的内联函数。

- **托管**

  选中时，添加托管类和头文件。 清除时，添加本地类和头文件。
