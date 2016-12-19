---
title: "添加成员变量向导 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.variable.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "添加成员变量向导 [C++]"
ms.assetid: 73e8fa99-ac1a-42e2-8fc2-4684b9eb6d4d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 添加成员变量向导
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

该向导将成员变量声明添加到头文件，根据具体的选项，它还可以将代码添加到 .cpp 文件。  使用该向导添加了成员变量后，可以在开发环境中编辑代码。  
  
 **访问**  
 设置对成员变量的访问。  访问修饰符是指定其他类对成员变量的访问的关键字。  有关指定访问的更多信息，请参见[成员访问控制](../cpp/member-access-control-cpp.md)。  默认情况下，成员变量的访问级别设置为 **public**。  
  
-   [public](../cpp/public-cpp.md)  
  
-   [protected](../cpp/protected-cpp.md)  
  
-   [private](../cpp/private-cpp.md)  
  
 **变量类型**  
 设置正在添加的成员变量的返回类型。  
  
-   如果正在添加的成员变量不是对话框控件，从可用类型列表中选择。  
  
     有关类型的信息，请参见[基本类型](../cpp/fundamental-types-cpp.md)。  
  
    |||  
    |-|-|  
    |`char`|**short**|  
    |**double**|`unsigned char`|  
    |**float**|`unsigned int`|  
    |`int`|`unsigned long`|  
    |**long**||  
  
-   如果正在添加对话框控件的成员变量，则此框中充满为控件或值返回的对象类型。  如果选择“控件”，则“变量类型”指定在“控件 ID”框中选择的控件的基类。  如果对话框控件可以包含值，则当选择“值”时，“变量类型”指定该控件可以包含的值的适当类型。  有关更多信息，请参见[对话框控件和变量类型](../ide/dialog-box-controls-and-variable-types.md)。  
  
     该值取决于“控件 ID”中的选定内容并且不能更改。  
  
 **变量名**  
 设置正在添加的成员变量的名称。  成员变量通常以标识字符串“m\_”开头，默认情况下会为您提供此标识字符串。  
  
 **控件变量**  
 指示成员变量在具有[数据交换和数据验证](../mfc/dialog-data-exchange-and-validation.md)支持的对话框内管理控件。  有关更多信息，请参见 [DoDataExchange](../Topic/CWnd::DoDataExchange.md)。  此选项仅对添加到从 [CDialog](../mfc/reference/cdialog-class.md) 导出的类的成员变量可用。  选择此框将激活“控件 ID”和“控件类型”选项。  
  
 **控件 ID**  
 设置正在添加的控件变量的 ID。  从列表中选择正在为其添加成员变量的控件类型的 ID。  列表仅在“控件变量”被选定框时是活动的，并且仅包含已添加到对话框的控件的 ID。  例如，对于标准的**“确定”**按钮，控件 ID 为 **IDOK**。  
  
|选项|说明|  
|--------|--------|  
|**控件**|默认情况下，为控件类型设置此选项。  它管理控件本身而非控件的状态或内容（当可能需要处理列表框、组合框或编辑框时）。|  
|**值**|此选项仅对可以包含值（如编辑框）或反映状态（如复选框）的控件类型可用，并且可以为其管理范围、内容或状态。  有关更多信息，请参见[对话框控件和变量类型](../ide/dialog-box-controls-and-variable-types.md)。|  
  
 **类别**  
 指定变量是基于控件类型还是控件的值。  
  
 **控件类型**  
 设置正在添加的控件类型。  此框不可更改。  例如，按钮的控件类型为 **BUTTON**，而组合框的控件类型为 **COMBOBOX**。  有关更多信息，请参见[对话框控件和变量类型](../ide/dialog-box-controls-and-variable-types.md)。  
  
 **最大字符数**  
 仅在“变量类型”设置为 [CString](../atl-mfc-shared/reference/cstringt-class.md) 时可用。  指示控件最多可以保留的字符数。  
  
 **最小值**  
 仅当变量类型为 **BOOL、**`int`、**UINT**、**long**、`DWORD`、**float**、**double**、**BYTE**、**short**、[COleCurrency](../mfc/reference/colecurrency-class.md) 或 [CTime](../atl-mfc-shared/reference/ctime-class.md) 时可用。  指示小数位数或日期范围可接受的最小值。  
  
 **最大值**  
 仅当变量类型为 **BOOL**、`int`、**UINT**、**long**、`DWORD`、**float**、**double**、**BYTE**、**short**、`COLECurrency` 或 `CTime` 时可用。  指示小数位数或日期范围可接受的最大值。  
  
 **.h 文件**  
 对于 ActiveX 控件，其成员变量要求包装类。  设置添加类声明的头文件名。  
  
 **.cpp 文件**  
 对于 ActiveX 控件，其成员变量要求包装类。  设置添加类定义的实现文件名。  
  
 **Comment**  
 提供成员变量头文件中的注释。  
  
## 请参阅  
 [添加成员变量](../ide/adding-a-member-variable-visual-cpp.md)