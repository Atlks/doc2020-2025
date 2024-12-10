Hitek sttb imprv vdx tishen retry


Retry 一般使用在http 上，有些时候io file also need 





global['retry']=retry;
function  retry(f,reTrytimes,chkFun)
{

   var rzt_fnl;
   for(let i=0;i<reTrytimes;i++)
   {
         rzt_fnl=f();
       if(chkFun(rzt_fnl))
           break;
   }

   return rzt_fnl;


}






retry(() => {
   return dsl_callFunCmdMode("oplog_qry")
}, 3, (rzt) => {
   try {
       json_decode(rzt);
       return true;
   } catch (e) {
       return fal;
   }
});

