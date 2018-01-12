---
title: "添加成员变量向导 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.variable.overview
dev_langs: C++
helpviewer_keywords: Add Member Variable Wizard [C++]
ms.assetid: 73e8fa99-ac1a-42e2-8fc2-4684b9eb6d4d
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b909ec7ccd830e088df81ca0b2db8cda133c7a20
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="add-member-variable-wizard"></a>添加成员变量向导
此向导将成员变量声明添加到标头文件，并根据的选项，它可以将代码添加到的.cpp 文件。 一旦已添加成员变量使用向导，你可以编辑在开发环境中的代码。  
  
 **访问**  
 设置的访问权限的成员变量。 访问修饰符是指定其他类都没有成员变量的访问权限的关键字。 请参阅[成员访问控制](../cpp/member-access-control-cpp.md)有关指定访问的详细信息。 成员变量的访问级别设置为**公共**默认情况下。  
  
-   [公用](../cpp/public-cpp.md)  
  
-   [受保护](../cpp/protected-cpp.md)  
  
-   [专用](../cpp/private-cpp.md)  
  
 **变量类型**  
 设置要添加的成员变量的返回类型。  
  
-   如果在添加不是对话框控件的成员变量，从可用类型列表中选择。  
  
     有关类型的信息，请参阅[基本类型](../cpp/fundamental-types-cpp.md)。  
  
    |||  
    |-|-|  
    |`char`|**short**|  
    |**double**|`unsigned char`|  
    |**float**|`unsigned int`|  
    |`int`|`unsigned long`|  
    |**long**||  
  
-   如果在添加对话框控件的成员变量，则此框填入为控件或值返回的对象的类型。 如果你选择**控件**，然后**变量类型**指定在控件中选择的基类**控件 ID**框。 如果对话框控件可以包含一个值，并且如果您选择**值**，然后**变量类型**指定控件可以包含的值的相应类型。 请参阅[对话框控件和变量类型](../ide/dialog-box-controls-and-variable-types.md)有关详细信息。  
  
     此值取决于在所选内容**控件 ID** ，不能更改。  
  
 **变量名称**  
 设置要添加的成员变量的名称。 成员变量通常以"m_，"默认情况下为你提供的标识字符串开头。  
  
 **控制变量**  
 指示成员变量在管理与对话框中的控件[数据交换和数据验证](../mfc/dialog-data-exchange-and-validation.md)支持。 请参阅[DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)有关详细信息。 此选项是仅适用于成员变量添加到类中派生自[CDialog](../mfc/reference/cdialog-class.md)。 选中此框可激活**控件 ID**和**控件类型**选项。  
  
 **控件 ID**  
 设置要添加的控制变量的 ID。 从列表中选择要为其添加成员变量的控件的类型的 ID。 该列表是活动时，才**控制变量**框处于选中状态，并且仅包含已添加到对话框中的控件的 Id。 例如，对于标准**确定**按钮，控件 ID 是**IDOK**。  
  
|选项|描述|  
|------------|-----------------|  
|**控件**|默认情况下，控件类型设置此选项。 它管理控件本身并不是状态或内容 （如你可能想要使用列表框、 组合框中或编辑框执行操作） 的控件。|  
|**“值”**|此选项才可用仅为控件类型可以包含一个值 （如编辑框中） 或反映状态 （例如复选框），并为其可能管理范围、 内容或状态。 请参阅[对话框控件和变量类型](../ide/dialog-box-controls-and-variable-types.md)有关详细信息。|  
  
 **类别**  
 指定变量根据控件类型或控件的值。  
  
 **控件类型**  
 设置要添加的控件的类型。 此框不可更改。 例如，一个按钮，具有的控件类型**按钮**，和组合框中具有的控件类型**COMBOBOX**。 请参阅[对话框控件和变量类型](../ide/dialog-box-controls-and-variable-types.md)有关详细信息。  
  
 **最大字符数**  
 时才可用**变量类型**设置为[CString](../atl-mfc-shared/reference/cstringt-class.md)。 指示最大的控件可以容纳的字符数。  
  
 **最小值**  
 仅当变量的类型时可用**BOOL**， `int`， **UINT**，**长**， `DWORD`， **float**， **double**，**字节**，**短**， [COLECurrency](../mfc/reference/colecurrency-class.md)或[CTime](../atl-mfc-shared/reference/ctime-class.md)。 指示可接受的小数位数或日期范围的最低值。  
  
 **最大值**  
 仅当变量的类型时可用**BOOL**， `int`， **UINT**，**长**， `DWORD`， **float**， **double**，**字节**，**短**，`COLECurrency`或`CTime`。 指示可接受的小数位数或日期范围的最高值。  
  
 **.h 文件**  
 对于 ActiveX 控件，其成员变量所需的包装类。 设置要添加的类声明的标头文件的名称。  
  
 **.cpp 文件**  
 对于 ActiveX 控件，其成员变量所需的包装类。 设置要添加的类定义的实现文件的名称。  
  
 **注释**  
 提供的成员变量的标头文件中的注释。  
  
## <a name="see-also"></a>请参阅  
 [添加成员变量](../ide/adding-a-member-variable-visual-cpp.md)