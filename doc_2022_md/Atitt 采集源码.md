Atitt 采集源码

Collage/api.htm

public function api($pp = [])

>>>  public function vod($param)
>>>  model('Collect')->vod_data($param,$res );


atal error: Uncaught exception 'think\exception\PDOException' with message 'SQLSTATE[22007]: Invalid datetime format: 1292 Incorrect datetime value: '' for column 'created_at' at row 1' in /var/www/html/thinkphp/library/think/db/Connection.php:462 Stack trace: #0 /var/www/html/thinkphp/library/think/db/Query.php(269): think\db\Connection->execute('INSERT INTO `ma...', Array, Object(think\db\Query)) #1 /var/www/html/thinkphp/library/think/db/Query.php(2275): think\db\Query->execute('INSERT INTO `ma...', Array, Object(think\db\Query)) #2 [internal function]: think\db\Query->insert(Array) #3 /var/www/html/thinkphp/library/think/Model.php(2190): call_user_func_array(Array, Array) #4 /var/www/html/application/common/model/Collect.php(673): think\Model->__call('insert', Array) #5 /var/www/html/application/common/model/Collect.php(673): app\common\model\Vod->insert(Array) #6 /var/www/html/application/admin/controller/Collect.php(274): app\common\model\Collect->vod_data(Array, Array) #7 /var/www/html/application/admin/controller in /var/www/html/thinkphp/library/think/db/Connection.php on line 462
