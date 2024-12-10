Tpscrt  自动扣费解决方案

Kehu,solu,soluPrice,expireTime


user表，balance

Up user set  balance=balance-soluPrice,op=autokofei  where now>expireTime


Log solu,use trigger...

If( op=autokofei  )
Insert log  
