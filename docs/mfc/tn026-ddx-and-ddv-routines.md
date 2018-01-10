---
title: "TN026: DDX 和 DDV 例程 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DDX
- DDV
dev_langs: C++
helpviewer_keywords:
- DDX (dialog data exchange), procedures
- TN026
- DDV (dialog data validation), procedures
ms.assetid: c2eba87a-4b47-4083-b28b-e2fa77dfb4c4
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 15c2309e8080892bdca2753c1ea6128ce419862f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="tn026-ddx-and-ddv-routines"></a>TN026：DDX 和 DDV 例程
> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 此说明描述的对话框数据交换 (DDX) 和对话框数据验证 (DDV) 体系结构。 它还介绍如何编写一个 DDX_ 或 DDV_ 过程以及如何将扩展 ClassWizard 用于您的例程。  
  
## <a name="overview-of-dialog-data-exchange"></a>对话框数据交换的概述  
 C + + 代码完成所有对话框数据函数。 没有任何特殊的资源或神奇的宏。 机制的核心是虚拟函数，它是类中重写每个对话框，没有对话框数据交换和验证。 始终，则该文件位于此窗体：  
  
```  
void CMyDialog::DoDataExchange(CDataExchange* pDX)  
{  
    CDialog::DoDataExchange(pDX);
*// call base class  
 *//{{AFX_DATA_MAP(CMyDialog)  
 <data_exchange_function_call>  
 <data_validation_function_call> *//}}AFX_DATA_MAP  
}  
```  
  
 特殊格式 AFX 注释允许 ClassWizard 定位和编辑此函数中的代码。 与 ClassWizard 不兼容的代码应放置在特殊格式注释之外中。  
  
 在上面的示例中，< data_exchange_function_call > 采用的形式：  
  
```  
DDX_Custom(pDX,
    nIDC,
    field);
```  
  
 和 < data_validation_function_call > 是可选的并采用的形式：  
  
```  
DDV_Custom(pDX,
    field, ...);
```  
  
 中每个可能包含多个 DDX_/DDV_ 对`DoDataExchange`函数。  
  
 有关所有对话框数据交换例程和 MFC 提供的对话框数据验证例程的列表，请参阅 afxdd_.h。  
  
 对话框数据就是： 中的成员数据**CMyDialog**类。 它不存储在结构或类似的任何内容。  
  
## <a name="notes"></a>说明  
 尽管我们中调用此"对话框数据"，所有功能都均可在任何类派生自`CWnd`并都不限于只需对话框。  
  
 在标准 c + + 中的构造函数，通常一个块以与中设置的数据的初始值`//{{AFX_DATA_INIT`和`//}}AFX_DATA_INIT`注释。  
  
 `CWnd::UpdateData`是操作执行的初始化和错误处理围绕对调用`DoDataExchange`。  
  
 你可以调用`CWnd::UpdateData`在任何时候执行数据交换和验证。 默认情况下`UpdateData`中默认值 (TRUE) 称为`CDialog::OnOK`处理程序和`UpdateData`(FALSE) 调用默认情况下`CDialog::OnInitDialog`。  
  
 DDV_ 例程应紧跟在 DDX_ 例程该*字段*。  
  
## <a name="how-does-it-work"></a>它是如何工作的  
 不需要了解以下以使用对话框数据。 但是，了解此后台进行的活动的工作原理将帮助你编写自己的 exchange 或验证过程。  
  
 `DoDataExchange`非常相似，成员函数即将`Serialize`成员函数-它是负责从外部的形式获取或设置数据，为/（在这种情况下控件在对话框中） 从/到类中的成员数据。 `pDX`参数是执行数据交换的上下文，它是类似于`CArchive`参数`CObject::Serialize`。 `pDX` (`CDataExchange`对象) 都有标志非常类似的方向`CArchive`方向标志：  
  
-   如果**！ m_bSaveAndValidate**，然后将数据状态加载到控件。  
  
-   如果`m_bSaveAndValidate`，然后从控件中设置数据状态。  
  
 验证仅发生时`m_bSaveAndValidate`设置。 值`m_bSaveAndValidate`由的 BOOL 参数`CWnd::UpdateData`。  
  
 有三个其他令人感兴趣`CDataExchange`成员：  
  
- `m_pDlgWnd`： 包含的控件窗口 （通常的对话）。 这是为了防止 DDX_ 和 DDV_ 全局函数的调用方无需将 this 传递到每个 DDX/DDV 例程。  
  
- `PrepareCtrl`和`PrepareEditCtrl`： 对话框控件准备数据交换。 将存储该控件的句柄将焦点设置在验证失败。 `PrepareCtrl`用于 nonedit 控件和`PrepareEditCtrl`用于编辑的控件。  
  
- **失败**： 提出消息框，提示用户输入错误后调用。 此例程会将焦点还原到的最后一个控件 (上次调用`PrepareCtrl` / `PrepareEditCtrl`)，并引发异常。 可以从 DDX_ 和 DDV_ 例程调用此成员函数。  
  
## <a name="user-extensions"></a>用户扩展  
 有多种方法来扩展默认的 DDX/DDV 机制。 你可以：  
  
-   添加新的数据类型。  
  
 ```  
    CTime 
 ```  
  
-   添加新的 exchange 过程 (DDX_)。  
  
 ```  
    void PASCAL DDX_Time(CDataExchange* pDX,
    int nIDC,
    CTime& tm);

 ```  
  
-   添加新的验证过程 (DDV_)。  
  
 ```  
    void PASCAL DDV_TimeFuture(CDataExchange* pDX,
    CTime tm,
    BOOL bFuture);
*// make sure time is in the future or past  
 ```  
  
-   将任意表达式传递给验证过程。  
  
 ```  
    DDV_MinMax(pDX,
    age,
    0,
    m_maxAge);

 ```  
  
    > [!NOTE]
    >  此类的任意表达式的 ClassWizard 无法编辑，因此应移动之外的特殊格式注释 (/ / {{AFX_DATA_MAP(CMyClass))。  
  
 具有**DoDialogExchange**成员函数包括条件语句或与混合交换和验证函数调用的任何其他有效的 c + + 语句。  
  
```  
//{{AFX_DATA_MAP(CMyClass)  
DDX_Check(pDX,
    IDC_SEX,
    m_bFemale);

DDX_Text(pDX,
    IDC_EDIT1,
    m_age);

//}}AFX_DATA_MAP  
if (m_bFemale)  
    DDV_MinMax(pDX,
    age,
    0,
    m_maxFemaleAge);

else  
    DDV_MinMax(pDX,
    age,
    0,
    m_maxMaleAge);
```  
  
> [!NOTE]
>  如上所示，此类代码的 ClassWizard 无法编辑，并应仅在特殊格式注释之外使用。  
  
## <a name="classwizard-support"></a>ClassWizard 支持  
 ClassWizard 支持 DDX/DDV 自定义项的子集，它允许你将自己 DDX_ 和 DDV_ 例程集成到 ClassWizard 用户界面。 如果你打算重新特定 DDX 和 DDV 例程的项目中或在许多项目中，执行此操作是唯一的成本有益。  
  
 若要执行此操作，需要将特殊条目 DDX 发出。CLW （以前版本的 Visual c + + 中 APSTUDIO 存储此信息。INI) 或你的项目中。CLW 文件。 特殊的条目可以输入在你的项目的 [常规信息] 部分。CLW 文件或的 DDX [ExtraDDX] 部分中。CLW files\microsoft Visual Studio\Visual C + + \bin 目录中的文件。 你可能需要创建 DDX。如果它尚不存在，则 CLW 文件。 如果你计划仅在特定的项目中使用的自定义的 DDX_/DDV_ 例程，则将条目添加到你的项目 [常规信息] 节。CLW 改为文件。 如果你计划在多个项目使用的例程，则将条目添加到 DDX [ExtraDDX] 部分。CLW。  
  
 这些特殊的项的常规格式为：  
  
```  
ExtraDDXCount=n  
```  
  
 其中 n 是要遵循的 ExtraDDX 行数  
  
```  
ExtraDDX=<keys>;<vb-keys>; <prompt>; <type>; <initValue>; <DDX_Proc>  
[;<DDV_Proc>; <prompt1>; <arg1>; [<prompt2>; <fmt2>]]  
```  
  
 其中是一个数字 1-n，该值指示正在定义的列表中的 DDX 类型。  
  
 由; 字符分隔每个字段。 如下所述的字段以及它们的用途。  
  
 \<密钥 >  
 =，该值指示哪些对话框控件的允许使用此变量的类型的单个字符的列表。  
  
 E = 编辑  
  
 C = 两个状态的复选框  
  
 c = 三态复选框  
  
 R = 组中的第一个单选按钮  
  
 L = 非排序的列表框  
  
 l = 已排序的列表框  
  
 M = （与编辑项） 的组合框  
  
 N = 非排序的下拉列表  
  
 n = 排序的下拉列表  
  
 1 = 如果 DDX 插入应添加到列表的开头 （默认值添加到结尾） 这通常适用于传输的控制属性的 DDX 例程。  
  
 \<vb 密钥 >  
 此字段用于仅在 16 位产品中 VBX 控件 （将 VBX 控件不支持在 32 位产品中）  
  
 \<提示符 >  
 字符串置于属性组合框 （无需加引号）  
  
 \<type>  
 类型在标头文件中发出的单个标识符。 在上面 DDX_Time 与我们示例，必须先将此设置为 CTime。  
  
 \<vb 密钥 >  
 不使用在此版本中，并且应始终为空  
  
 \<initValue >  
 初始值-0 或空。 如果它为空，然后将 //{{AFX_DATA_INIT 部分实现文件中不写入任何初始化行。 空白条目应该用于 c + + 对象 (如`CString`， `CTime`，依次类推) 具有构造函数，它能够保证正确初始化。  
  
 < DDX_Proc >  
 DDX_ 过程单个标识符。 C + + 函数名称必须以"DDX_，"开头，但不在 < DDX_Proc > 标识符中包含"DDX_"。 在上面的示例中，< DDX_Proc > 标识符将时间。 当 ClassWizard 写入函数调用中的实现文件 {{AFX_DATA_MAP 部分中，它将追加此名称到 DDX_，因此到达 DDX_Time。  
  
 \<注释 >  
 要在具有此 DDX 变量的对话框中显示的注释。 放置任何你想要在这里，和通常提供的内容的文本描述由 DDX/DDV 对执行的操作。  
  
 < DDV_Proc >  
 该条目的 DDV 部分是可选的。 并非所有的 DDX 例程具有相应 DDV 例程。 通常情况下，它会更方便，包括传输的必要组成部分验证阶段。 通常这种情况时 DDV 例程不需要任何参数，因为 ClassWizard 不支持不带任何参数的 DDV 例程。  
  
 \<arg >  
 DDV_ 过程单个标识符。 C + + 函数名称必须以"DDV_"开头，但不是包括"DDX_"中的 < DDX_Proc > 标识符。  
  
 后跟 1 或 2 DDV 参数：  
  
 \<promptX >  
 要编辑的项目 （使用和快捷键） 之上放置字符串  
  
 \<fmtX >  
 参数的类型之一的的格式字符  
  
 d = int  
  
 u = 无符号  
  
 D = 长整型 （即，长时间）  
  
 U = 无符号长时间 (即，DWORD)  
  
 f = float  
  
 F = double  
  
 s = 字符串  
  
## <a name="see-also"></a>请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

