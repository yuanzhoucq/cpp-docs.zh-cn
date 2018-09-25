---
title: 一般 C++ 类向导 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.class.generic
dev_langs:
- C++
helpviewer_keywords:
- Generic C++ Class Wizard [C++]
ms.assetid: aa95be9e-fc1b-45db-a11d-0d32c4929077
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b104c0631fde3164ef4299cead47caba912874b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431081"
---
# <a name="generic-c-class-wizard"></a>泛型 C++ 类向导

将一般 C++ 类向导添加到项目。 该类不从 ATL 或 MFC 继承。

- **类名**

   设置新类的名称。

- **.h 文件**

   为新类的头文件设置名称。 默认情况下，此名称基于你在“类名”中提供的名称。 要将头文件保存至所选择的位置，或将类声明追加到现有文件，请单击省略号按钮 (...)。如果指定现有文件，则单击“完成”时，向导会提示你指定是否要将该类声明追加至文件的内容中。 要追加该声明，请单击“是”；要返回至向导并指定另一个文件名，请单击“否”。

- **.cpp 文件**

   为新类的实现文件设置名称。 默认情况下，此名称基于你在“类名”中提供的名称。 要将该实现文件保存至所选择的位置，或将类声明追加到现有文件，请单击省略号按钮 (...)。如果选择现有文件的名称，当你单击“完成”时，向导会提示你指定是否要将该类定义追加至文件的内容中。 要追加该定义，请单击“是”；要返回至向导并指定另一个文件名，请单击“否”。

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

## <a name="see-also"></a>请参阅

[添加一般 C++ 类](../ide/adding-a-generic-cpp-class.md)