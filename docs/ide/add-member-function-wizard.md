---
title: 添加成员函数向导 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.function.overview
dev_langs:
- C++
helpviewer_keywords:
- Add Member Function Wizard [C++]
ms.assetid: 13b6defc-faa6-4d57-83db-9dd854cbea3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 488c7ca455b267a79b0d2906849596346a191792
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332392"
---
# <a name="add-member-function-wizard"></a>添加成员函数向导
此向导将成员函数声明添加到头文件，并将存根成员函数实现添加到所选类的实现文件中。  
  
 如果使用此向导添加了成员函数，则可在开发环境中编辑代码。  
  
 **返回类型**  
 设置要添加的成员函数的返回类型。 可自行提供返回类型，或者从可用类型列表中进行选择。 有关类型的更多信息，请参阅[基础类型](../cpp/fundamental-types-cpp.md)。  
  
||||  
|-|-|-|  
|`char`|`int`|`unsigned int`|  
|**double**|**long**|`unsigned long`|  
|**float**|**short**|`void`|  
|`HRESULT`|`unsigned char`||  
  
 **函数名**  
 设置要添加的成员函数的名称。  
  
 **参数类型**  
 如果成员函数具有参数，则设置要为成员函数添加的参数的类型。 可自行提供参数类型，或者从可用类型列表中进行选择。  
  
||||  
|-|-|-|  
|`char`|`int`|`unsigned char`|  
|**double**|**long**|`unsigned int`|  
|**float**|**short**|`unsigned long`|  
  
 **参数名称**  
 如果成员函数具有参数，则设置要为成员函数添加的参数的名称。  
  
 **参数列表**  
 显示已添加到成员函数的参数列表。 要将参数添加到列表中，请在“参数类型”和“参数名称”框中提供类型和名称，然后单击“添加”。 要从列表中删除参数，请选择该参数，然后单击“删除”。  
  
 **访问**  
 设置成员函数的访问权限。 访问修饰符是一种关键字，用于指定其他类对该成员函数的访问权限。 若要详细了解如何指定访问权限，请参阅[成员访问控件](../cpp/member-access-control-cpp.md)。 成员函数的访问级别默认情设置为“公共”。  
  
-   [公共](../cpp/public-cpp.md)  
  
-   [已保护](../cpp/protected-cpp.md)  
  
-   [专用](../cpp/private-cpp.md)  
  
 检查新的成员函数是静态的还是虚拟的，以及它是内联函数还是纯函数。 如果将成员函数设置为纯函数，则选中 `Virtual` 复选框，且“内联”复选框不可用。 默认为非静态、非虚拟的成员函数。  
  
|选项|描述|  
|------------|-----------------|  
|[静态](../cpp/storage-classes-cpp.md)|指定该函数的作用类似于全局函数且可在类外调用（即使没有类实例化）。 成员函数无权访问非静态成员。 指定为 `Static` 的成员函数不能是虚拟函数。|  
|[虚拟](../cpp/virtual-cpp.md)|确保无论用于进行成员函数调用的表达式如何，均为对象调用正确的成员函数。 指定为 `Virtual` 的成员函数不能是静态函数。|  
|**纯**|指示不实现正在声明的虚拟成员函数，因此，只能在虚拟成员函数上指定“纯”。 包含纯虚拟成员函数（至少一个）的类被视为抽象类。 从抽象类中派生的类必须实现纯虚拟成员函数，或其自身也必须是抽象类。|  
|[内联](../cpp/inline-functions-cpp.md)|指示编译器将成员函数体的副本插入到每个调用成员函数的位置。 指定为“内联”的成员函数不能是纯函数。|  
  
 **.cpp 文件**  
 设置写入存根成员函数实现的文件位置。 它默认写入到添加成员函数的类的 .cpp 文件中。 单击省略号按钮更改文件名。 成员函数实现会添加到所选文件的内容中。  
  
 **注释**  
 在成员函数的头文件中提供注释。  
  
 **函数签名**  
 单击“完成”时，按代码中的显示方式显示成员函数。 无法编辑此框中的文本。 要更改成员函数，请在向导中更改相应的框。  
  
## <a name="see-also"></a>另请参阅  
 [添加成员函数](../ide/adding-a-member-function-visual-cpp.md)