---
title: "测试只读提供程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, calling
- OLE DB providers, testing
ms.assetid: e4aa30c1-391b-41f8-ac73-5270e46fd712
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 438ab42a7f0f12379621a591f3b0b1eeb5930afd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="testing-the-read-only-provider"></a>测试只读提供程序
若要测试提供程序，你需要使用者。 如果使用者可以与相匹配的提供程序，它可以帮助。 OLE DB 使用者模板不 OLE DB 的精简包装，并与提供程序的 COM 对象匹配。 因为源附带的使用者模板，可以很轻松地调试具有它们的提供程序。 使用者模板也是开发使用者应用程序的非常小且快速方法。  
  
 本主题中的示例为测试使用者创建默认 MFC 应用程序向导应用程序。 测试应用程序是一条包含添加的 OLE DB 使用者模板代码的简单对话框。  
  
### <a name="to-create-the-test-application"></a>若要创建测试应用程序  
  
1.  在 **“文件”** 菜单上，单击 **“新建”**，然后单击 **“项目”**。  
  
2.  在项目类型窗格中，选择**Visual c + + 项目**文件夹。 在模板窗格中，选择**MFC 应用程序**。  
  
3.  项目名称，输入**TestProv**，然后单击**确定**。  
  
     MFC 应用程序向导出现。  
  
4.  上**应用程序类型**页上，选择**基于对话框**。  
  
5.  上**高级功能**页上，选择**自动化**，然后单击**完成**。  
  
> [!NOTE]
>  如果你添加该应用程序不需要自动化支持**CoInitialize**中**CTestProvApp::InitInstance**。  
  
 你可以查看和编辑 TestProv 对话框中 (IDD_TESTPROV_DIALOG) 通过在资源视图中选择它。 将两个列表框中，一个用于在行集中，每个字符串放在对话框中。 关闭排序属性的同时按 ALT + Enter 选中的列表框后，单击列表框**样式**选项卡，然后清除**排序**复选框。 另外，放置**运行**按钮在对话框中，以获取文件。 完成的 TestProv 对话框中应具有两个分别; 标记为"字符串 1"和"字符串 2"的列表框它还具有**确定**，**取消**，和**运行**按钮。  
  
 打开对话框类 （在此案例 TestProvDlg.h) 的标头文件。 将以下代码添加到标头文件 （在外部的任何类声明）：  
  
```  
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
  
 该代码表示定义列将包含在行集中的用户记录。 当客户端调用**IAccessor::CreateAccessor**，它使用这些条目来指定要绑定的列。 OLE DB 使用者模板还允许你要动态绑定列。 COLUMN_ENTRY 宏是 PROVIDER_COLUMN_ENTRY 宏的客户端版本。 两个 COLUMN_ENTRY 宏指定序号、 类型、 长度和数据成员的两个字符串。  
  
 添加的处理程序函数**运行**按住 ctrl 键并双击按钮**运行**按钮。 在函数中将以下代码：  
  
```  
///////////////////////////////////////////////////////////////////////  
// TestProvDlg.cpp  
  
void CtestProvDlg::OnRun()  
{  
   CCommand<CAccessor<CProvider> > table;  
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
  
 `CCommand`， `CDataSource`，和`CSession`所有属于 OLE DB 使用者模板的类。 每个类模仿提供程序中的 COM 对象。 `CCommand`对象采用`CProvider`在标头文件中，作为模板参数声明的类。 `CProvider`参数表示用于从提供程序访问数据的绑定。 下面是`Open`数据源、 会话和命令的代码：  
  
```  
if (source.Open("MyProvider.MyProvider.1", NULL) != S_OK)  
   return;  
  
if (session.Open(source) != S_OK)  
   return;  
  
if (table.Open(session, _T("c:\\samples\\myprov\\myData.txt")) != S_OK)  
   return;  
```  
  
 要打开的每个类中的行创建提供程序中的每个 COM 对象。 若要查找提供程序，请使用提供程序的 ProgID。 你可以从系统注册表或通过查找 MyProvider.rgs 文件来获取 ProgID （打开提供程序的目录并搜索 ProgID 密钥）。  
  
 附带 MyProv 示例 MyData.txt 文件了。 若要创建你自己的文件，请使用编辑器，并键入偶数数目的字符串，每个字符串之间按 enter 键。 如果移动文件，请更改的路径名称。  
  
 传入的字符串"c:\\\samples\\\myprov\\\MyData.txt"中`table.Open`行。 如果单步执行`Open`调用，你将看到此字符串传递给`SetCommandText`提供程序中的方法。 请注意，`ICommandText::Execute`方法使用该字符串。  
  
 若要提取的数据，调用`MoveNext`表上。 `MoveNext`调用**irowset:: Getnextrows**， `GetRowCount`，和`GetData`函数。 当有更多的行时 (即，在行集中当前位置大于`GetRowCount`)，循环将终止：  
  
```  
while (table.MoveNext() == S_OK)  
{  
   m_ctlString1.AddString(table.szField1);  
   m_ctlString2.AddString(table.szField2);  
}  
```  
  
 请注意，当存在更多的行时，提供程序将返回**DB_S_ENDOFROWSET**。 **DB_S_ENDOFROWSET**值不是一个错误。 你应始终检查针对`S_OK`若要取消数据提取循环并不使用 SUCCEEDED 宏。  
  
 你现在应能够生成并测试该程序。  
  
## <a name="see-also"></a>请参阅  
 [增强简单的只读提供程序](../../data/oledb/enhancing-the-simple-read-only-provider.md)