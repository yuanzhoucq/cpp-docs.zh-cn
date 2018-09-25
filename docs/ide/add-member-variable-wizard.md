---
title: 添加成员变量向导 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.variable.overview
dev_langs:
- C++
helpviewer_keywords:
- Add Member Variable Wizard [C++]
ms.assetid: 73e8fa99-ac1a-42e2-8fc2-4684b9eb6d4d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4d4518a48d51e6187015dc3fd7b5456e04e1ae84
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45701527"
---
# <a name="add-member-variable-wizard"></a>添加成员变量向导
此向导将成员变量声明添加到头文件，并且根据选项，它可能会将代码添加到 .cpp 文件。 如果使用此向导添加了成员变量，则可以在开发环境中编辑代码。  
  
- **访问**

   设置成员变量的访问权限。 访问修饰符是一种关键字，用于指定其他类对该成员变量的访问权限。 若要详细了解如何指定访问权限，请参阅[成员访问控件](../cpp/member-access-control-cpp.md)。 成员变量的访问级别在默认情况下设为“公共”。  
  
-   [public](../cpp/public-cpp.md)  
  
-   [protected](../cpp/protected-cpp.md)  
  
-   [private](../cpp/private-cpp.md)  
  
- **变量类型**

   设置要添加的成员变量的返回类型。  
  
   - 如果所要添加的成员变量不是对话框控件，请从可用类型列表中进行选择。  
  
      有关类型的更多信息，请参阅[基础类型](../cpp/fundamental-types-cpp.md)。  
  
      |||  
      |-|-|  
      |**char**|**short**|  
      |**double**|**unsigned char**|  
      |**float**|**unsigned int**|  
      |**int**|**unsigned long**|  
      |**long**||  
  
   - 如果要添加一个对话框控件的成员变量，则此框填入控件或值的返回对象的类型。 如果选择“控件”，则“变量类型”指定在“控件 ID”框中选择的控件的基类。 如果对话框控件可以包含一个值并选择“值”，则“变量类型”指定控件可以包含的值的适当类型。 请参阅[对话框控件和变量类型](../ide/dialog-box-controls-and-variable-types.md)，了解更多信息。  
  
      此值取决于在“控件 ID”中所选的内容，且无法更改。  
  
- **变量名**

   设置要添加的成员变量的名称。 成员变量通常以可识别的字符串“m_,”开头，此字符串会作为默认内容为你提供。  
  
- **控件变量**

   指示成员变量在具有[数据交换和数据验证](../mfc/dialog-data-exchange-and-validation.md)支持的对话框中管理控件。 请参阅 [DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) 以获取详细信息。 此选项仅能用于向派生自 [CDialog](../mfc/reference/cdialog-class.md) 的类添加的成员变量。 选择此框以激活“控件 ID”和“控件类型”选项。  
  
- **控件 ID**

   为要添加的控件变量设置 ID。 从要为其添加成员变量的控件类型的 ID 列表中进行选择。 该列表仅在选中“控件变量”时为活动状态，且仅包含已添加到对话框的控件 ID。 例如，对于标准的“确定”按钮，控件 ID 为“IDOK”。  
  
   |选项|描述|  
   |------------|-----------------|  
   |**控件**|此选项为控件类型的默认设置选项。 它管理控件本身，而不是控件的状态或内容（就像你想使用列表框、组合框活编辑框执行操作）。|  
   |**值**|此选项仅可用于能包含值的控件类型（例如编辑框）或能反映状态的控件类型（例如复选框），并且可能会为它们管理范围、内容或状态。 请参阅[对话框控件和变量类型](../ide/dialog-box-controls-and-variable-types.md)，了解更多信息。|  
  
- **类别**

   指定变量基于控件类型还是控件的值。  
  
- **控件类型**

   设置要添加的控件类型。 此框不可更改。 例如，按钮的控件类型为 BUTTON，而组合框的控件类型为 COMBOBOX。 请参阅[对话框控件和变量类型](../ide/dialog-box-controls-and-variable-types.md)，了解更多信息。  
  
- **最大字符数**

   仅当“变量类型”设为 [CString](../atl-mfc-shared/reference/cstringt-class.md) 时可用。 表示控件能容纳的最大字符数。  
  
- **最小值**

   仅当变量类型为 BOOL、`int`、UINT、long、`DWORD`、float、double、BYTE、short、[COLECurrency](../mfc/reference/colecurrency-class.md) 或 [CTime](../atl-mfc-shared/reference/ctime-class.md) 时可用。 表示规模或日期范围可接受的最小值。  
  
- **最大值**

   仅当变量类型为 BOOL、`int`、UINT、long、`DWORD`、float、double、BYTE、short、`COLECurrency` 或 `CTime` 时可用。 表示规模或日期范围可接受的最大值。  
  
- **.h 文件**

   用于 ActiveX 控件，该控件的成员变量需要一个包装类。 设置头文件的名称以便添加类声明。  
  
- **.cpp 文件**

   用于 ActiveX 控件，该控件的成员变量需要一个包装类。 设置实现文件的名词以便添加类声明。  
  
- **注释**

   在成员变量的头文件中提供注释。  
  
## <a name="see-also"></a>请参阅  
 [添加成员变量](../ide/adding-a-member-variable-visual-cpp.md)