Atitit 数据库性能提升 异步sql



MySQL更新延遲-這只是我的解決方案
問題
MySQL支持將DELAYED選項作為INSERT語句使用，但是由於某些晦澀的原因，到目前為止還沒有人知道，它不支持UPDATE DELAYED或DELETE DELAYED。


可以insert delay 然后使用trigger update delete即可

