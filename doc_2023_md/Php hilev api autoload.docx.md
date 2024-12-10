Php hilev api autoload



没有函数的函数自动加载器。您有四种现实的解决方案：

将所有函数包装到命名空间类中（上下文适当）。假设您有一个名为 的函数string_get_letters。StringFunctions您可以将其添加到称为静态函数的类中。因此，string_get_letters()您可以拨打 ，而不是拨打StringFunctions::get_letters()。然后您将使用__autoload那些命名空间类。


预加载所有功能。由于您使用的是类，因此不应该有那么多函数，因此只需预加载它们即可。


在使用函数之前加载它们。在每个文件中，require_once将在该文件中使用的函数文件。


首先不要使用函数。如果您正在开发 OOP 代码（无论如何，您似乎就是这样），那么应该几乎不需要函数。您需要一个（或多个）函数来完成的所有事情，您都可以以面向对象的方式构建并避免对函数的需要。

就我个人而言，我建议根据您的具体需求以及代码库的质量和大小选择 1、2 或 4...




// Your custom class dir
    define('CLASS_DIR', 'class/')

    // Add your class dir to include path
    set_include_path(get_include_path().PATH_SEPARATOR.CLASS_DIR);

    // You can use this trick to make autoloader look for commonly used "My.class.php" type filenames
    spl_autoload_extensions('.class.php');

    // Use default autoload implementation
    spl_autoload_register();


使用 spl 提供的 __autoload 队列注册一个函数。如果队列尚未激活，它将被激活。
如果您的代码具有现有的__autoload()函数，则必须在 __autoload 队列上显式注册该函数。这是因为spl_autoload_register()将通过spl_autoload()或 spl_autoload_call()有效地替换__autoload()函数的引擎缓存。
如果必须有多个自动加载函数，spl_autoload_register() 可以实现这一点。它有效地创建了一个自动加载函数队列，并按照定义的顺序运行每个函数。相比之下， __autoload()只能定义一次。

