Vs2012 wkfl  workflow、



确定用于创作自定义活动的基活动类
下表列出了自定义活动基类中可用的功能。



使用 CodeActivity 类创作工作流活动 - .NET Framework |Microsoft学习


    internal class HelloActivity : CodeActivity
    {
     protected override void Execute(CodeActivityContext context)
        {
            Console.WriteLine("Hello from myAct1! ");
        }
    }
 


已启动生成...
1>------ 已启动生成: 项目: ActivityLibrary1, 配置: Debug Any CPU ------
1>  ActivityLibrary1 -> C:\Users\attil\source\repos\WindowsFormsApp2\ActivityLibrary1\bin\Debug\ActivityLibrary1.dll


使用 CodeActivityContext
可以使用 CodeActivityContext 类型的参数成员从 Execute 方法中访问工作流运行时的功能。通过 CodeActivityContext 提供的功能包括：context

获取和设置变量和参数的值。


使用跟踪的自定义跟踪功能。


使用 GetProperty 访问活动的执行属性。

工具箱项 添加的自定义活动的程序集

打开工作流解决方案。 从“工具”菜单中选择“选择工具箱项” 。 在“选择工具箱项”对话框中，选择“System.Activities 组件”选项卡，然后单击“浏览”导航到包含要添加的自定义活动的程序集 。 选择该程序集，然后单击“确定”。 自定义活动组件将添加到组件列表中并自动处于选中状态
如果jiazai cant dll..maybe class not public...public is just ok.




对工作流项目使用自定义活动

将宿主项目中的引用添加到包含自定义活动的活动库项目中。


生成解决方案。


若要在设计器中使用自定义活动，请在工具箱中找到自定义活动，然后将该活动拖到设计器图面上。




