---
title: 测试只读提供程序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, calling
- OLE DB providers, testing
ms.assetid: e4aa30c1-391b-41f8-ac73-5270e46fd712
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4630391d9bce319c35af18767d7133bd34a92362
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2018
ms.locfileid: "49990199"
---
# <a name="testing-the-read-only-provider"></a>测试只读提供程序

若要测试的提供程序，需要使用者。 如果使用者可以与提供程序，它可以帮助。 OLE DB 使用者模板 OLE DB 的薄包装器，与提供程序的 COM 对象相匹配。 因为源随使用者模板，很容易地调试提供程序使用它们。 使用者模板也是开发使用者应用程序的非常小巧快捷方式。  
  
本主题中的示例为测试使用者创建一个默认 MFC 应用程序向导应用程序。 测试应用程序是一个简单的对话框，其中添加 OLE DB 使用者模板代码。  
  
## <a name="to-create-the-test-application"></a>若要创建测试应用程序  
  
1. 在 **“文件”** 菜单上，单击 **“新建”**，然后单击 **“项目”**。  
  
1. 在中**项目类型**窗格中，选择**Visual c + + 项目**文件夹。 在中**模板**窗格中，选择**MFC 应用程序**。  
  
1. 输入项目名称*TestProv*，然后单击**确定**。  
  
     MFC 应用程序向导出现。  
  
1. 上**应用程序类型**页上，选择**基于对话框**。  
  
1. 上**高级功能**页上，选择**自动化**，然后单击**完成**。  
  
> [!NOTE]
> 如果添加该应用程序不需要自动化的支持`CoInitialize`在`CTestProvApp::InitInstance`。  
  
你可以查看和编辑**TestProv**对话框 (IDD_TESTPROV_DIALOG) 中选择该**资源视图**。 将两个列表框中，一个用于在行集中，每个字符串放置在对话框中。 关闭排序属性的同时按列表框**Alt**+**Enter**选中列表框后，单击**样式**选项卡，并清除**排序**复选框。 另外，放置**运行**按钮在对话框中，以获取文件。 已完成**TestProv**对话框中应具有两个列表框分别标记为"String 1"和"字符串 2"; 它还具有**确定**，**取消**，和**运行**按钮。  
  
打开对话框类 （在此事例 TestProvDlg.h) 的标头文件。 以下代码添加到标头文件 （在外部的任何类声明）：  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// TestProvDlg.h  
  
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
  
该代码表示定义列将为行集中的用户记录。 当客户端调用`IAccessor::CreateAccessor`，它使用这些项来指定要绑定的列。 OLE DB 使用者模板还可用于动态绑定列。 COLUMN_ENTRY 宏是 PROVIDER_COLUMN_ENTRY 宏的客户端的版本。 两个 COLUMN_ENTRY 宏指定序号、 两个字符串的类型、 长度和数据成员。  
  
添加的处理程序函数**运行**通过按按钮**Ctrl** ，然后双击**运行**按钮。 将以下代码放在函数中：  
  
```cpp
///////////////////////////////////////////////////////////////////////  
// TestProvDlg.cpp  
  
void CtestProvDlg::OnRun()  
{  
   CCommand<CAccessor<CProvider>> table;  
   CDataSource source;  
   CSession   session;  
  
   if (source.Open("MyProvider.MyProvider.1", NULL) != S_OK)  
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
  
`CCommand`， `CDataSource`，和`CSession`所有属于 OLE DB 使用者模板的类。 每个类模仿该提供程序中的 COM 对象。 `CCommand`对象采用`CProvider`在标头文件中，作为模板参数声明的类。 `CProvider`参数表示用于从提供程序访问数据的绑定。 下面是`Open`数据源、 会话和命令的代码：  
  
```cpp  
if (source.Open("MyProvider.MyProvider.1", NULL) != S_OK)  
   return;  
  
if (session.Open(source) != S_OK)  
   return;  
  
if (table.Open(session, _T("c:\\samples\\myprov\\myData.txt")) != S_OK)  
   return;  
```  
  
要打开的每个类中的行在提供程序中创建的每个 COM 对象。 若要查找的提供者，请使用`ProgID`的提供程序。 可以获取`ProgID`系统注册表中或通过查看 MyProvider.rgs 文件中 (打开提供程序的目录并搜索`ProgID`密钥)。  
  
MyData.txt 文件随`MyProv`示例。 若要创建你自己的文件，请使用编辑器，并键入偶数数目的字符串，每个字符串之间按 enter 键。 如果将文件移动，更改路径名称。  
  
在字符串中传递"c:\\\samples\\\myprov\\\MyData.txt"中`table.Open`行。 如果单步执行`Open`调用时，你将看到此字符串将传递到`SetCommandText`提供程序中的方法。 请注意，`ICommandText::Execute`方法使用该字符串。  
  
若要提取的数据，调用`MoveNext`表上。 `MoveNext` 调用`IRowset::GetNextRows`， `GetRowCount`，和`GetData`函数。 有没有更多行时 (即，行集中当前位置大于`GetRowCount`)，循环将终止：  
  
```cpp  
while (table.MoveNext() == S_OK)  
{  
   m_ctlString1.AddString(table.szField1);  
   m_ctlString2.AddString(table.szField2);  
}  
```  
  
请注意，如果没有更多行，提供程序返回 DB_S_ENDOFROWSET。 DB_S_ENDOFROWSET 值不是错误。 您应始终检查针对要取消数据提取循环，而不使用 SUCCEEDED 宏，则为 S_OK。  
  
现在应能够生成并测试该程序。  
  
## <a name="see-also"></a>请参阅  

[增强简单的只读提供程序](../../data/oledb/enhancing-the-simple-read-only-provider.md)