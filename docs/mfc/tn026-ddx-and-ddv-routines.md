---
title: TN026:DDX 和 DDV 例程
ms.date: 06/28/2018
f1_keywords:
- DDX
- DDV
helpviewer_keywords:
- DDX (dialog data exchange), procedures
- TN026
- DDV (dialog data validation), procedures
ms.assetid: c2eba87a-4b47-4083-b28b-e2fa77dfb4c4
ms.openlocfilehash: 89916e60d9677240f2d70e37e9a80e6ad7a76fc3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305861"
---
# <a name="tn026-ddx-and-ddv-routines"></a>TN026:DDX 和 DDV 例程

> [!NOTE]
> 以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

此说明描述的对话框数据交换 (DDX) 和对话框数据验证 (DDV) 体系结构。 它还介绍了如何编写一个 DDX_ 或 DDV_ 过程以及如何扩展类向导以使用你的例程。

## <a name="overview-of-dialog-data-exchange"></a>对话框数据交换的概述

完成所有对话框数据函数C++代码。 没有任何特殊资源或神奇的宏。 该机制的核心是虚拟函数，它是类中重写每个对话框中，没有对话框数据交换和验证。 它始终位于此窗体中：

```cpp
void CMyDialog::DoDataExchange(CDataExchange* pDX)
{
    CDialog::DoDataExchange(pDX);   // call base class

    //{{AFX_DATA_MAP(CMyDialog)
        <data_exchange_function_call>
        <data_validation_function_call>
    //}}AFX_DATA_MAP
}
```

特殊格式 AFX 评论功能允许 ClassWizard 定位和编辑此函数中的代码。 与 ClassWizard 不兼容的代码应放置在特殊格式注释之外。

在上述示例中， \<data_exchange_function_call > 的格式：

```cpp
DDX_Custom(pDX, nIDC, field);
```

和\<data_validation_function_call > 是可选的在窗体：

```cpp
DDV_Custom(pDX, field, ...);
```

中每个可能包含多个 DDX_/DDV_ 对`DoDataExchange`函数。

所有对话框数据交换例程和 MFC 提供的对话框数据验证例程的列表，请参阅 afxdd_.h。

对话框数据只是： 中的成员数据`CMyDialog`类。 它不存储在结构或类似内容。

## <a name="notes"></a>说明

虽然我们调用此"对话框数据"，但所有功能都都可在派生自任何类中`CWnd`并都不限于只是对话框。

初始数据值设置在标准C++构造函数中包含的块通常`//{{AFX_DATA_INIT`并`//}}AFX_DATA_INIT`注释。

`CWnd::UpdateData` 是操作执行的初始化和错误处理围绕对调用`DoDataExchange`。

您可以调用`CWnd::UpdateData`在任何时间执行数据交换和验证。 默认情况下`UpdateData`(TRUE) 调用中的默认`CDialog::OnOK`处理程序和`UpdateData`在默认的调用 (FALSE) `CDialog::OnInitDialog`。

DDV_ 例程应立即为此，遵循 DDX_ 例程*字段*。

## <a name="how-does-it-work"></a>它是如何工作的

不需要了解以下以使用对话框数据。 但是，了解这在后台的工作原理将帮助您编写自己的 exchange 或验证过程。

`DoDataExchange`成员函数是非常类似于`Serialize`成员函数-它是负责外部窗体中获取或设置数据/（控件在对话框中，在这种情况下） 从/向类中的成员数据。 *PDX*参数是执行数据交换的上下文，它是类似于`CArchive`参数`CObject::Serialize`。 *PDX* (`CDataExchange`对象) 都有方向标志非常类似`CArchive`方向标志：

- 如果`!m_bSaveAndValidate`，然后加载到控件的数据状态。

- 如果`m_bSaveAndValidate`，然后从控件中设置的数据状态。

仅发生验证时`m_bSaveAndValidate`设置。 值`m_bSaveAndValidate`由对的 BOOL 参数`CWnd::UpdateData`。

有三个其他有趣的`CDataExchange`成员：

- `m_pDlgWnd`：包含控件的窗口 （通常的对话）。 这是为了防止 DDX_ 和 DDV_ 全局函数的调用方无需将 this 传递到每个 DDX/DDV 例程。

- `PrepareCtrl`和`PrepareEditCtrl`:准备用于数据交换的对话框控件。 存储该控件的句柄将焦点设置在验证失败。 `PrepareCtrl` 用于非编辑控件和`PrepareEditCtrl`用于编辑控件。

- `Fail`：将一个消息框，提醒用户输入错误后调用。 此例程会将焦点还原到最后一个控件 (上次调用`PrepareCtrl`或`PrepareEditCtrl`)，并引发异常。 可以从 DDX_ 和 DDV_ 例程调用此成员函数。

## <a name="user-extensions"></a>用户扩展

有几种方法来扩展默认的 DDX/DDV 机制。 你可以：

- 添加新的数据类型。

    ```cpp
    CTime
    ```

- 添加新的 exchange 过程 (DDX_)。

    ```cpp
    void PASCAL DDX_Time(CDataExchange* pDX, int nIDC, CTime& tm);
    ```

- 添加新的验证过程 (DDV_)。

    ```cpp
    void PASCAL DDV_TimeFuture(CDataExchange* pDX, CTime tm, BOOL bFuture);
    // make sure time is in the future or past
    ```

- 将任意表达式传递给验证过程。

    ```cpp
    DDV_MinMax(pDX, age, 0, m_maxAge);
    ```

    > [!NOTE]
    > 此类的任意表达式的类向导无法编辑，因此应移动之外的特殊格式注释 (/ / {{AFX_DATA_MAP(CMyClass))。

具有`DoDialogExchange`成员函数包括条件语句或任何其他有效C++语句与混合的交换和验证函数调用。

```cpp
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
> 如上所示，此类代码的类向导无法编辑，因此应仅之外的特殊格式的注释。

## <a name="classwizard-support"></a>类向导支持

类向导允许您将自己 DDX_ 和 DDV_ 例程集成到类向导用户界面，从而支持 DDX/DDV 自定义项的子集。 执行此操作是有益的唯一成本，如果你打算重复使用在项目中或在许多项目中的特定 DDX 和 DDV 例程。

若要执行此操作，DDX 中进行特殊的输入。CLW (以前版本的视觉对象C++APSTUDIO 中存储此信息。INI) 或在项目中。CLW 文件。 可以是特殊的条目，输入你的项目的 [常规信息] 部分中。CLW 文件或 [ExtraDDX] 节的 DDX。在 \Program Files\Microsoft Visual Studio\Visual CLW 文件C++\bin 目录。 您可能需要创建 DDX。CLW 文件，如果它尚不存在。 如果你计划仅在某个项目中使用自定义 DDX_/DDV_ 例程，将条目添加到你的项目 [常规信息] 节。CLW 改为文件。 如果您计划在多个项目使用的例程，将条目添加到 DDX [ExtraDDX] 部分。CLW。

这些特殊的项的常规格式为：

> ExtraDDXCount=*n*

其中*n*是 ExtraDDX 数目？ 行要遵循的窗体

> ExtraDDX?=*keys*; *vb-keys*; *prompt*; *type*; *initValue*; *DDX_Proc* [; *DDV_Proc*; *prompt1*; *arg1* [; *prompt2*; *fmt2*]]

其中？ 是一个数字 1- *n* ，该值指示正在定义的列表中的 DDX 类型。

由; 字符分隔每个字段。 字段和它们的用途如下所述。

- *keys*

  单个字符，该值指示哪个对话框控件的允许使用此变量的类型的列表。

  |字符|允许的控件|
  |-|-|
  E | 编辑
  C | 两个状态的复选框
  c | 三态复选框
  R | 在组中的第一个单选按钮
  L | 非排序的列表框
  l | 已排序的列表框
  M | 组合框 （具有编辑项）
  N | 排序的下拉列表中
  n | 排序的下拉列表中
  1 | DDX 插入是否应添加到列表的开头 （默认值添加到结尾） 这通常用于传输的控制属性的 DDX 例程。

- *vb-keys*

  此字段用于仅在 16 位产品 VBX 控件 （VBX 控件不支持在 32 位产品）

- *提示*

  要将放置在属性组合框 （无引号） 的字符串

- *type*

  类型在标头文件中发出的单个标识符。 在上述示例使用 DDX_Time 中，必须先将此设置为 CTime。

- *vb-keys*

  不使用此版本中，应始终为空

- *initValue*

  初始价值-0 或空。 如果它为空，将 //{{AFX_DATA_INIT 部分的实现文件中不写入任何初始化行。 空白条目应使用的C++对象 (如`CString`， `CTime`，依此类推) 的有保证正确初始化的构造函数。

- *DDX_Proc*

  DDX_ 过程的单个标识符。 C++函数名称必须以"DDX_，"开头，但不包含"DDX_"中\<DDX_Proc > 标识符。 在上述示例中， \<DDX_Proc > 标识符将时间。 当 ClassWizard 将写入到实现文件中的函数调用 {{AFX_DATA_MAP 部分中，它将追加此名称到 DDX_，因此到达 DDX_Time。

- *comment*

  若要在具有此 DDX 变量的对话框中显示的注释。 将你想在这里，并且通常提供一些内容描述由 DDX/DDV 对执行的操作的任何文本。

- *DDV_Proc*

  该条目的 DDV 部分是可选的。 并非所有的 DDX 例程具有相应 DDV 例程。 通常情况下，它是更方便地传输的过程中不可或缺包括验证阶段。 这通常是当 DDV 例程不需要任何参数，因为 ClassWizard 不支持不带任何参数的 DDV 例程。

- *arg*

  DDV_ 过程的单个标识符。 C++函数名称必须以"DDV_"开头，但不是包括"DDX_"中\<DDX_Proc > 标识符。

  *arg*后跟 1 或 2 个 DDV 参数：

   - *promptN*

      若要编辑的项目 (& 加速器) 之上放置的字符串。

   - *fmtN*

      Arg 类型之一的格式字符：

      |字符|类型|
      |-|-|
      |d | int|
      |u | unsigned int|
      |D | long int （即，长时间）|
      |U | 无符号长时间 (即，DWORD)|
      |f | float|
      |F | double|
      |秒 | string|

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
