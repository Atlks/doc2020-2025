Secury fun 验证或清理
该扩展通过验证或清理数据来过滤数据。当数据源包含像用户提供的输入数据等未知（或外部）数据时，这尤其有用。例如，这些数据可能来自 HTML 表单。 
有两种主要的过滤类型：验证（validation）和清理（sanitization）。 
验证用于验证或检查数据是否符合某些条件。例如，传递 FILTER_VALIDATE_EMAIL 可以确定数据是否是有效的电子邮件地址，但不会更改数据本身。 
清理将清理数据，因此可能通过移除不需要的字符来改变数据。例如，使用 FILTER_SANITIZE_EMAIL 会移除电子邮件地址中不适当的字符。也就是说，不会对数据进行验证。 
filter_has_var — 检测是否存在指定类型的变量
filter_id — 返回与某个特定名称的过滤器相关联的id
filter_input_array — 获取一系列外部变量，并且可以通过过滤器处理它们
filter_input — 通过名称获取特定的外部变量，并且可以通过过滤器处理它
filter_list — 返回所支持的过滤器列表
filter_var_array — 获取多个变量并且过滤它们
filter_var — 使用特定的过滤器过滤一个变量


Sql和html脚本encode
