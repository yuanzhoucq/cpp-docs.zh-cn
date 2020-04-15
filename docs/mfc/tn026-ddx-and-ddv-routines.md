---
title: TN026：DDX 和 DDV 例程
ms.date: 06/28/2018
f1_keywords:
- DDX
- DDV
helpviewer_keywords:
- DDX (dialog data exchange), procedures
- TN026
- DDV (dialog data validation), procedures
ms.assetid: c2eba87a-4b47-4083-b28b-e2fa77dfb4c4
ms.openlocfilehash: 711d433b51ca09836f372d09a11f86c28b82cce6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370338"
---
# <a name="tn026-ddx-and-ddv-routines"></a>TN026：DDX 和 DDV 例程

> [!NOTE]
> 以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

本说明描述了对话框数据交换 （DDX） 和对话框数据验证 （DDV） 体系结构。 它还描述了如何编写DDX_或DDV_过程，以及如何扩展 ClassWizard 来使用例程。

## <a name="overview-of-dialog-data-exchange"></a>对话数据交换概述

所有对话框数据函数都使用C++代码完成。 没有特殊的资源或神奇的宏。 机制的核心是一个虚拟函数，该函数在每个执行数据交换和验证的对话框类中都会被覆盖。 它始终以此形式找到：

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

特殊格式的 AFX 注释允许 ClassWizard 在此函数中查找和编辑代码。 与 ClassWizard 不兼容的代码应放置在特殊格式注释之外。

在上面的示例中，data_exchange_function_call>\<的形式是：

```cpp
DDX_Custom(pDX, nIDC, field);
```

并且\<data_validation_function_call>是可选的，并且的形式是：

```cpp
DDV_Custom(pDX, field, ...);
```

每个`DoDataExchange`函数中可能包含多个DDX_/DDV_对。

有关 MFC 提供的所有对话数据交换例程和对话框数据验证例程的列表，请参阅"afxdd_.h"。

对话框数据就是：`CMyDialog`类中的成员数据。 它不存储在结构或类似的东西中。

## <a name="notes"></a>说明

尽管我们称之为"对话框数据"，但所有功能都可用于派生自`CWnd`的任何类，并且不仅限于对话框。

数据的初始值设置在标准C++构造函数中，通常位于 带`//{{AFX_DATA_INIT`和`//}}AFX_DATA_INIT`注释的块中。

`CWnd::UpdateData`是在 调用 周围执行初始化和错误处理的操作`DoDataExchange`。

您可以随时调用`CWnd::UpdateData`以执行数据交换和验证。 默认情况下`UpdateData`，在默认`CDialog::OnOK`处理程序中调用 （TRUE），`UpdateData`并在默认值`CDialog::OnInitDialog`中调用 （FALSE）。

DDV_例程应立即遵循该*字段*的DDX_例程。

## <a name="how-does-it-work"></a>它是如何工作的

使用对话框数据不需要了解以下内容。 但是，了解此操作方式将有助于确保您编写自己的交换或验证过程。

`DoDataExchange`成员函数与`Serialize`成员函数非常类似 - 它负责从类中的成员数据获取或设置数据到/从外部窗体（在本例中为对话框中的控件）。 *pDX*参数是执行数据交换的上下文，`CArchive`与 的`CObject::Serialize`参数类似 。 *pDX（* 对象`CDataExchange`）具有非常类似于`CArchive`具有方向标志的方向标志：

- 如果`!m_bSaveAndValidate`，则将数据状态加载到控件中。

- 如果`m_bSaveAndValidate`，则从控件设置数据状态。

仅在设置验证时`m_bSaveAndValidate`进行验证。 的值`m_bSaveAndValidate`由 BOOL 参数确定到`CWnd::UpdateData`。

还有其他三个有趣的`CDataExchange`成员：

- `m_pDlgWnd`：包含控件的窗口（通常是对话框）。 这是为了防止DDX_的调用方，DDV_全局函数必须将"此"传递给每个 DDX/DDV 例程。

- `PrepareCtrl`和`PrepareEditCtrl`：为数据交换准备对话框控件。 存储控件的句柄，用于在验证失败时设置焦点。 `PrepareCtrl`用于非编辑控件，`PrepareEditCtrl`用于编辑控件。

- `Fail`：在启动一个消息框以提醒用户输入错误后调用。 此例程将焦点还原到最后一个控件（最后一个调用`PrepareCtrl``PrepareEditCtrl`或 ），并引发异常。 可以从DDX_和DDV_例程调用此成员函数。

## <a name="user-extensions"></a>用户扩展

有几种方法可以扩展默认的 DDX/DDV 机制。 可以：

- 添加新数据类型。

    ```cpp
    CTime
    ```

- 添加新的交换过程（DDX_）。

    ```cpp
    void PASCAL DDX_Time(CDataExchange* pDX, int nIDC, CTime& tm);
    ```

- 添加新的验证过程（DDV_）。

    ```cpp
    void PASCAL DDV_TimeFuture(CDataExchange* pDX, CTime tm, BOOL bFuture);
    // make sure time is in the future or past
    ```

- 将任意表达式传递给验证过程。

    ```cpp
    DDV_MinMax(pDX, age, 0, m_maxAge);
    ```

    > [!NOTE]
    > 此类任意表达式不能由 ClassWizard 编辑，因此应移至特殊格式注释之外（//{AFX_DATA_MAP（CMyClass））。

让`DoDialogExchange`成员函数包括条件或任何其他有效的C++语句与混合交换和验证函数调用。

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
> 如上所述，ClassWizard 不能编辑此类代码，并且只能在特殊格式注释之外使用。

## <a name="classwizard-support"></a>类向导支持

ClassWizard 允许您将自己的DDX_和DDV_例程集成到 ClassWizard 用户界面中，从而支持 DDX/DDV 自定义的子集。 只有当您计划在项目或许多项目中重用特定的 DDX 和 DDV 例程时，这样做才具有成本效益。

为此，在 DDX 中制作特殊条目。CLW（早期版本的视觉C++将此信息存储在 APSTUDIO 中。INI）或您的项目的 。CLW 文件。 特殊条目可以在项目的 [常规信息] 部分中输入。CLW 文件或 DDX 的 [额外DDX] 部分。CLW 文件在 [程序文件]微软可视化工作室\视觉C++\bin 目录中。 您可能需要创建 DDX。CLW 文件（如果不存在）。 如果计划仅在特定项目中使用自定义DDX_/DDV_例程，请将条目添加到项目的 [常规信息] 部分。而是 CLW 文件。 如果计划在多个项目上使用例程，则将条目添加到 DDX 的 [ExtraDDX] 部分。CLW.

这些特殊条目的一般格式是：

> 额外DDXCount**n*

*n*是额外 DDX 的数量？行遵循，形式

> 额外DDX？**键*;*vb 键*;*提示*;*类型*;*initValue*;*DDX_Proc**DDV_Proc;**提示1;**arg1* *;*提示2;**fmt2*[]

哪里？ 是数字 1 - *n，* 指示正在定义的列表中键入哪个 DDX 类型。

每个字段都由";"字符分隔。 下面将介绍字段及其用途。

- *钥匙*

  允许单个字符列表，指示此变量类型的对话框控件。

  |字符|允许的控制|
  |-|-|
  E | 编辑
  C | 双状态复选框
  c | 三州复选框
  R | 组中的第一个单选按钮
  L | 未排序的列表框
  l | 排序列表框
  M | 组合框（带编辑项目）
  N | 非排序的放置列表
  n | 排序放置列表
  1 | 如果 DDX 插入应添加到列表头（默认添加到尾），这通常用于传输"控制"属性的 DDX 例程。

- *vb 键*

  此字段仅用于 VBX 控件的 16 位产品（32 位产品不支持 VBX 控件）

- *提示*

  字符串放在属性组合框中（无引号）

- *type*

  用于在标头文件中发出的类型的单个标识符。 在上面的DDX_Time示例中，这将设置为 CTime。

- *vb 键*

  此版本中未使用，应始终为空

- *initValue*

  初始值 = 0 或空白。 如果为空，则在实现文件的 //_AFX_DATA_INIT 部分不会写入初始化行。 空白条目应用于具有保证正确初始化的构造函数`CString`C++`CTime`对象（如 、等）。

- *DDX_Proc*

  DDX_过程的单个标识符。 C++函数名称必须以"DDX_"开头，但不要在\<DDX_Proc>标识符中包含"DDX_"。 在上面的示例中，DDX_Proc>\<标识符将是时间。 当 ClassWizard 将函数调用写入 {AFX_DATA_MAP 节中的实现文件时，它将此名称追加到DDX_，从而到达DDX_Time。

- *评论*

  注释以在此 DDX 的变量对话框中显示。 放置任何您喜欢的文本，通常提供描述 DDX/DDV 对执行的操作的内容。

- *DDV_Proc*

  条目的 DDV 部分是可选的。 并非所有 DDX 例程都有相应的 DDV 例程。 通常，将验证阶段作为传输的组成部分变得更加方便。 当 DDV 例程不需要任何参数时，通常会出现这种情况，因为 ClassWizard 不支持没有任何参数的 DDV 例程。

- *精 氨 酸*

  DDV_过程的单个标识符。 C++函数名称必须以"DDV_"开头，但在\<DDX_Proc>标识符中不包括"DDX_"。

  *arg*后跟 1 或 2 DDV args：

  - *提示N*

      要放置在编辑项上方的字符串（&用于加速器）。

  - *fmtN*

      arg 类型的格式字符，其中之一：

      |字符|类型|
      |-|-|
      |d | int|
      |u | unsigned int|
      |D | 长因（即长）|
      |U | 长无符号（即DWORD）|
      |f | FLOAT|
      |F | double|
      |s | 字符串|

## <a name="see-also"></a>另请参阅

[技术说明（按编号）](../mfc/technical-notes-by-number.md)<br/>
[按类别分类的技术说明](../mfc/technical-notes-by-category.md)
