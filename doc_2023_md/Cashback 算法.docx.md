Cashback 算法

获取cashback最后的时间

function get_lastFsDttm(userid) {
   let visa = getLoginToken()
   let dbdir = __dirname + "/../db/" + visa.agtid + "/";
   let dbf = dbdir + "cashbackLog.json"

   //  let dbf = __dirname + "/../db_zhudan/zhudan_uid" + user.data.userid;
   console.log(dbf)
   let dtRows = pdo_query({"userid": userid}, dbf)
   if (!dtRows)
       return new Date("2000-01-01")
   if (dtRows.length == 0)
       return new Date("2000-01-01")
   dtRows.sort(function (a, b) {
       return a.tmstmp - b.tmstmp
   });

   return new Date(dtRows[0].dttm);
}


筛选 sum 计算总的流水鹅（uid,lastFsDt）

function newSumBet(userid,lastFsDttm) {

   let dbf = __dirname + "/../db_zhudan/zhudan_uid" + userid + ".json";
   console.log(dbf)
   let dtRows = readFileAsJsonV2(dbf, [])

   let selectRows = dtRows.filter((e) => {
       if (new Date(e.GameStartTime) > lastFsDttm)
           return true;
   })

   return sumColV3("ValidBet", selectRows)


}

getThisTimeCashbackAmt

function getThisTimeCashbackAmt(userid, fsRat) {
   // const allbet = sumColV2((e) => e.ValidBet, dtRows)

   const lastFsDttm = get_lastFsDttm(userid)
   const allbet = newSumBet(userid,lastFsDttm);
   const feshweiAmt = allbet * fsRat;
   const alreadyFsAmt = get_alreadyFsAmtV2(userid);

   let dbgobj = {"uidx": userid, "allbet": allbet, "feshweiAmt": feshweiAmt, "alreadyFsAmt": alreadyFsAmt}
   console.log(JSON.stringify(dbgobj))

   let fsFnl = feshweiAmt;//  - alreadyFsAmt
   if (fsFnl <= 0)
       fsFnl = 0
   fsFnl = nbr_fmt_fix2(fsFnl)
   return {allbet, alreadyFsAmt, fsFnl};
}

