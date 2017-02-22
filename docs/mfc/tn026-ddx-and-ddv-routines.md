---
title: "TN026：DDX 和 DDV 例程 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DDX"
  - "DDV"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DDV（对话框数据验证）, 过程"
  - "对话框数据交换 (DDX), 过程"
  - "TN026"
ms.assetid: c2eba87a-4b47-4083-b28b-e2fa77dfb4c4
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# TN026：DDX 和 DDV 例程
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。  因此，某些过程和主题可能已过时或不正确。  要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 此注释说明对话框数据交换 \(DDX\) 和对话框数据验证 \(DDV\) 体系结构。  还描述如何编写 DDX\_ 或 DDV\_ 过程，以及如何扩展类向导用于例程。  
  
## 对话框数据交换的概述。  
 所有的对话框数据函数完成与 C\+\+ 代码。  无特殊的资源或魔术宏。  机制的重点不是在每一对话框类重写执行对话框数据交换和验证的虚函数。  它始终被找到以此形式：  
  
```  
void CMyDialog::DoDataExchange(CDataExchange* pDX)  
{  
    CDialog::DoDataExchange(pDX);    // call base class  
  
    //{{AFX_DATA_MAP(CMyDialog)  
        <data_exchange_function_call>  
        <data_validation_function_call>  
    //}}AFX_DATA_MAP  
}  
```  
  
 特定格式 AFX 注释允许 ClassWizard 定位和编辑此函数中的代码。  代码与兼容 ClassWizard 应放置在特殊形式注释。  
  
 在上面的示例中，\<data\_exchange\_function\_call\> 窗体：  
  
```  
DDX_Custom(pDX, nIDC, field);  
```  
  
 并 \<data\_validation\_function\_call\> 是可选的和形式：  
  
```  
DDV_Custom(pDX, field, ...);  
```  
  
 多个 DDX\_\/DDV\_对在每个 `DoDataExchange` 可以包含函数。  
  
 为任何对话框数据交换 \(DDE\) 例程和对话框数据验证例程参见“列表 afxdd\_.h”随 MFC。  
  
 对话框数据是：在 **CMyDialog** 类的数据成员。  在类似的结构或的任何未存储。  
  
## 注释  
 尽管我们调用此数据“对话框”，所有功能可在派生自 `CWnd` 的任何类和没有限制到对话框。  
  
 初始值数据中标准 C\+\+ 构造函数设置，通常在具有 `//{{AFX_DATA_INIT` 和 `//}}AFX_DATA_INIT` 的注释块。  
  
 `CWnd::UpdateData` 是在调用来执行初始化和错误处理对 `DoDataExchange`的操作。  
  
 可以随时调用 `CWnd::UpdateData` 进行数据交换和验证。  默认 `UpdateData`\(真\) 在默认 `CDialog::OnOK` 处理程序和 `UpdateData`。默认调用 `CDialog::OnInitDialog`\(错误\) 调用。  
  
 DDV\_ 例程应紧跟该 *字段的*DDX\_ 例程。  
  
## 它如何工作？  
 不需要了解下面即可使用对话框数据。  但是，了解这如何在后台工作可帮助您编写自己交换或验证过程。  
  
 `DoDataExchange` 成员函数非常类似 `Serialize` 成员函数 \(它获取或设置与应用\/或窗体外部 \(在本例在对话框的控件中的数据从运行\)\/至在类的数据成员。  参数 `pDX` 是执行上下文数据交换和参数与 `CArchive` 类似于 `CObject::Serialize`。  `pDX` \( `CDataExchange` 对象\)。具有方向标记就像具有方向 `CArchive` 标志：  
  
-   如果 **\!m\_bSaveAndValidate**，然后为控件状态加载数据。  
  
-   如果 `m_bSaveAndValidate`，然后将从控件的数据状态。  
  
 在设置 `m_bSaveAndValidate` 时，只验证发生。  `m_bSaveAndValidate` 的值取决于 `CWnd::UpdateData`的 BOOL 参数。  
  
 有其他 `CDataExchange` 的三个成员：  
  
-   `m_pDlgWnd`:包含控件的窗口 \(通常对话框\)。  这是为了避免全局函数。必须通过的 this”为每个 DDX\_ DDX\/DDV 例程和 DDV\_ 的调用方。  
  
-   `PrepareCtrl`和 `PrepareEditCtrl`:控件用于一对话框数据交换准备。  存储的设置焦点该手柄，并且在验证失败。  `PrepareCtrl` 为 nonedit 控件使用，而 `PrepareEditCtrl` 用于编辑控件。  
  
-   **未通过**:调用在引发通知用户的消息之后。输入错误。  该例程将焦点还原到最后一控件 \(从 `PrepareCtrl`\/`PrepareEditCtrl`\) 最后调用并引发异常。  该成员函数。从 DDX\_ 和 DDV\_ 例程调用。  
  
## 用户扩展  
 有多种方法来扩展默认 DDX\/DDV 机制。  您可以：  
  
-   添加新数据类型。  
  
    ```  
    CTime  
    ```  
  
-   添加新的 DDX\_ 交换过程 \(???\)。  
  
    ```  
    void PASCAL DDX_Time(CDataExchange* pDX, int nIDC, CTime& tm);  
    ```  
  
-   新添加的验证过程 DDV\_ \(???\)。  
  
    ```  
    void PASCAL DDV_TimeFuture(CDataExchange* pDX, CTime tm, BOOL bFuture);  
    // make sure time is in the future or past  
    ```  
  
-   传递任意表达式来验证过程。  
  
    ```  
    DDV_MinMax(pDX, age, 0, m_maxAge);  
    ```  
  
    > [!NOTE]
    >  这样任意表达式不受"编辑并 ClassWizard 不得将在特定格式注释外 \(\/\/ {AFX\_DATA\_MAP \(CMyClass\)\)。  
  
 具有 **DoDialogExchange** 成员函数包括条件或任何其他的有效 C\+\+ 语句用交互进行交换和验证函数调用。  
  
```  
//{{AFX_DATA_MAP(CMyClass)  
DDX_Check(pDX, IDC_SEX, m_bFemale);  
DDX_Text(pDX, IDC_EDIT1, m_age);  
//}}AFX_DATA_MAP  
if (m_bFemale)  
    DDV_MinMax(pDX, age, 0, m_maxFemaleAge);  
else  
    DDV_MinMax(pDX, age, 0, m_maxMaleAge);  
```  
  
> [!NOTE]
>  如上所述，此代码不受 ClassWizard 编辑，只应在特定格式注释。  
  
## ClassWizard 支持  
 ClassWizard 可以集成支持的子集 DDX\/DDV 自定义您自己 DDX\_ 和 DDV\_ 到例程 ClassWizard 用户界面。  如果打算重新使用特殊 DDX 和 DDV 例程在项目或在多项目，这样做只花费有利的。  
  
 若要执行此，特定输入在 DDX.CLW \(Visual C\+\+ 版本存储在 APSTUDIO.INI 的此信息\) 或项目中 .CLW 文件。  特定输入可以输入在项目的 .CLW 文件的通用信息。\] 部分或在 DDX.CLW 文件的节 \[ExtraDDX\] \\Program Files\\Microsoft Visual Studio\\Visual C \+\+\\bin 目录中。  如果不存在，您可能需要创建 DDX.CLW 文件。  如果您在某项目计划只使用自定义 DDX\_\/DDV\_例程中，将项添加到项目 .CLW 文件的 \[通用信息\] 部分。  如果您计划对许多项目的例程，添加输入到 DDX.CLW 的 \[ExtraDDX\] 部分。  
  
 这些输入特定常规格式为：  
  
```  
ExtraDDXCount=n  
```  
  
 n 位置是数字 ExtraDDX?下面的行  
  
```  
ExtraDDX?=<keys>;<vb-keys>; <prompt>; <type>; <initValue>; <DDX_Proc>  
[;<DDV_Proc>; <prompt1>; <arg1>; [<prompt2>; <fmt2>]]  
```  
  
 位置？第 N 是 1 \- 指示 DDX 输入定义列表。  
  
 每个字段通过分隔“;”字符。  字段及其用途介绍。  
  
 \<键\>  
 \= 指示单字符的列表的对话框此控制变量的类型。  
  
 13，E \= 编辑  
  
 C\# \= 两个状态复选框  
  
 c \= 三种状态复选框  
  
 \= R 首先单选按钮组中  
  
 左 \= nonsorted 列表框  
  
 \= l 排序列表框  
  
 \= M 组合框 \(与编辑项\)  
  
 " \= nonsorted 拉列表  
  
 n \= 排序的下拉列表  
  
 对于通常 DDX 例程使用传输“控件的”属性 \= 1，如果插入 DDX 应被添加到列表默认 \(开头是向尾\)。  
  
 \<VB 键\>  
 此字段仅用于控件 \(VBX 产品在 16 位 VBX 控件在 32 位产品不支持\)  
  
 \<提示\>  
 中的字符串。属性组合框 \(不是引号\)  
  
 \<type\>  
 单个类型的标识符可以发出在头文件。  在上面的示例中，我们 DDX\_Time 与这将设置为 CTime。  
  
 \<VB 键\>  
 不使用此版本，应总是为空  
  
 \<initValue\>  
 初始值 \- 0 或 null。  如果为空白，则初始化行写入不在\/\/{实现文件的 AFX\_DATA\_INIT 节。  为保证该具有构造函数正确的初始值的 C\+\+ 对象使用空白输入 \(如 `CString`，`CTime`，等等\)。  
  
 \<DDX\_Proc\>  
 DDX\_ 过程的唯一标识符。  C\+\+ 函数名称必须以“DDX\_ 开头，”，但不包括“DDX\_”在 \<DDX\_Proc\> 标识符。  在上面的示例中，\<DDX\_Proc\> 标识符是时间。  当 ClassWizard 编写函数调用。在中实现文件{AFX\_DATA\_MAP 节，它附加此名称为 DDX\_，从而达到 DDX\_Time。  
  
 \<注释\>  
 注释显示在对话框使用此变量的 DDX。  放置希望此处的所有文本和通常提供描述 DDX\/DDV 对执行的操作\)。  
  
 \<DDV\_Proc\>  
 输入的 DDV 部分是可选的。  不是所有的 DDX 例程具有相应的 DDV 例程。  通常，是非常方便。包括阶段验证作为转发的组成部分。  这通常是这样，因此 DDV 例程不需要任何参数时，因为类向导不支持 DDV 例程不带任何参数。  
  
 \<arg\>  
 DDV\_ 过程的唯一标识符。  C\+\+ 函数名称必须以“DDV\_”开头，但不包括“DDX\_”在 \<DDX\_Proc\> 标识符。  
  
 后跟 1 或 2 DDV args:  
  
 \<promptX\>  
 为位置的字符串在编辑项上 \( & 与快捷键\)  
  
 \<fmtX\>  
 arg 类型的格式字符，一  
  
 \= d int  
  
 \= u 未签名  
  
 \= D 长期 int \(即\)。  
  
 \= U 长时间未签名 \(即一\)  
  
 f 为浮点数  
  
 双重 F \=  
  
 \= 字符串。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)