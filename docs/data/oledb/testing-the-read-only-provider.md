---
title: 测试只读提供程序
ms.date: 11/04/2016
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, calling
- OLE DB providers, testing
ms.assetid: e4aa30c1-391b-41f8-ac73-5270e46fd712
ms.openlocfilehash: dc3c4ea36aa9dac64f2aa7861fd5d51927c77ecd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209491"
---
# <a name="testing-the-read-only-provider"></a>测试只读提供程序

若要测试提供程序，需要使用者。 如果使用者可以与提供程序相匹配，则可帮助。 OLE DB 使用者模板是围绕提供程序 COM 对象 OLE DB 和匹配的精简包装器。 由于源是使用使用者模板附带的，因此可以很容易地使用它们调试提供程序。 使用者模板也是开发使用者应用程序的一种非常小且快捷的方式。

本主题中的示例将为测试使用者创建默认的 MFC 应用程序向导应用程序。 测试应用程序是一个简单的对话框，其中添加了 OLE DB 使用者模板代码。

## <a name="to-create-the-test-application"></a>创建测试应用程序

1. 在“文件”菜单上，单击“新建”，然后单击“项目”。

1. 在 "**项目类型**" 窗格中，选择**安装**的 > **Visual C++**  > **MFC/ATL**文件夹。 在 "**模板**" 窗格中，选择 " **MFC 应用程序**"。

1. 对于 "项目名称"，请输入 " *TestProv*"，然后单击 **"确定"** 。

   **MFC 应用程序**向导随即出现。

1. 在 "**应用程序类型**" 页上，选择 "**基于对话框**"。

1. 在 "**高级功能**" 页上，选择 "**自动化**"，然后单击 "**完成**"。

> [!NOTE]
> 如果在 `CTestProvApp::InitInstance`中添加 `CoInitialize`，应用程序不需要自动化支持。

您可以通过在**资源视图**中选择**TestProv**对话框（IDD_TESTPROV_DIALOG）来查看和编辑该对话框。 将两个列表框（行集中的每个字符串对应一个列表框）放置在对话框中。 通过按**Alt**+在列表框处于选中状态时**输入**，并将**排序**属性设置为**False**，可以关闭两个列表框的排序属性。 此外，请在对话框中放置一个 "**运行**" 按钮，以获取该文件。 "完成的**TestProv** " 对话框中应有两个分别标记为 "string 1" 和 "string 2" 的列表框;它还包含 **"确定"、"** **取消**" 和 "**运行**" 按钮。

打开对话框类的标头文件（在本例中为 TestProvDlg）。 将以下代码添加到头文件（在任何类声明之外）：

```cpp
////////////////////////////////////////////////////////////////////////
// TestProvDlg.h
#include <atldbcli.h>  

class CProvider
{
// Attributes
public:
   char   szField1[16];
   char   szField2[16];

   // Binding Maps
BEGIN_COLUMN_MAP(CProvider)
   COLUMN_ENTRY(1, szField1)
   COLUMN_ENTRY(2, szField2)
END_COLUMN_MAP()
};
```

此代码表示一个用户记录，用于定义行集中将包含的列。 当客户端调用 `IAccessor::CreateAccessor`时，它将使用这些项来指定要绑定的列。 OLE DB 使用者模板还允许您动态绑定列。 COLUMN_ENTRY 的宏是 PROVIDER_COLUMN_ENTRY 宏的客户端版本。 这两个 COLUMN_ENTRY 宏指定两个字符串的序号、类型、长度和数据成员。

通过按**Ctrl**并双击 "**运行**" 按钮，为 "**运行**" 按钮添加处理程序函数。 将以下代码放入函数：

```cpp
///////////////////////////////////////////////////////////////////////
// TestProvDlg.cpp

void CTestProvDlg::OnRun()
{
   CCommand<CAccessor<CProvider>> table;
   CDataSource source;
   CSession session;

   if (source.Open("Custom.Custom.1", NULL) != S_OK)
      return;

   if (session.Open(source) != S_OK)
      return;

   if (table.Open(session, _T("c:\\samples\\myprov\\myData.txt")) != S_OK)
      return;

   while (table.MoveNext() == S_OK)
   {
      m_ctlString1.AddString(table.szField1);
      m_ctlString2.AddString(table.szField2);
   }
}
```

`CCommand`、`CDataSource`和 `CSession` 类都属于 OLE DB 使用者模板。 每个类模仿提供程序中的 COM 对象。 `CCommand` 对象采用标头文件中声明的 `CProvider` 类作为模板参数。 `CProvider` 参数表示用于访问提供程序中的数据的绑定。

用于打开每个类的行在提供程序中创建每个 COM 对象。 若要找到该提供程序，请使用该提供程序的 `ProgID`。 可以从系统注册表或通过查看自定义 .rgs 文件获取 `ProgID` （打开提供程序的目录并搜索 `ProgID` 键）。

`MyProv` 示例附带了 MyData 文件。 若要创建自己的文件，请使用编辑器并键入偶数个字符串，并在每个字符串之间按**enter** 。 如果移动该文件，请更改路径名称。

传入 `table.Open` 行中的字符串 "c：\\\samples\\\myprov\\\MyData.txt"。 如果单步执行 `Open` 调用，将看到此字符串传递到提供程序中的 `SetCommandText` 方法。 请注意，`ICommandText::Execute` 方法使用该字符串。

若要获取数据，请对表调用 `MoveNext`。 `MoveNext` 调用 `IRowset::GetNextRows`、`GetRowCount`和 `GetData` 函数。 如果没有更多的行（即，行集中的当前位置大于 `GetRowCount`），循环将终止。

如果没有更多的行，则提供程序将返回 DB_S_ENDOFROWSET。 DB_S_ENDOFROWSET 值不是错误。 应始终对 S_OK 进行检查以取消数据提取循环，而不是使用 SUCCEEDED 宏。

现在应能够生成并测试该程序。

## <a name="see-also"></a>另请参阅

[增强简单的只读提供程序](../../data/oledb/enhancing-the-simple-read-only-provider.md)
