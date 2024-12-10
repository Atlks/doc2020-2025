Im api bp tlgrm

Msg just a callfun cmd

Fun  parms1 p2 p3 

require("./recv.js")
msg_recvListen(token,msg_recv)



/**
* shfen rcv msg
* @param msg
*/
async function msg_recv(msg, bot) {
   log_fun_enter(arguments)
   console.log(msg)
   let txt = msg.text;
   let arr = txt.split(" ")
   let fun = arr[0]
   if (file_exists("./" + fun + "tlgrm.js")) {
       requirex(fun + ".js")
       requirex(fun + "tlgrm.js")
       let acc = msg.from.username

       let argarr = [];
       argarr.push(msg)

       let rzt = await call_func(fun, argarr)

       console.log("[msg_recv ] ret=>" + rzt)
   } else {
       //if nml msg ,add user first
       let acc = msg.from.username
       let nknm = msg.from.first_name
       addUser(acc, nknm)
   }


}

